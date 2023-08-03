---
tags:
	- en
	- database
	- softwareDesign
	- Neon
---
# Neon + Postgres.js: The Perfect Combo for Your MVP Project
I was choosing the tech stack for a small MVP project. I went with a familiar backend framework [Nest.js](https://nestjs.com/). But I wanted to do something new regarding the DB. 

In this particular project I had to develop a feature that would let users import a bunch of CSV files and then generate a huge table out of the data. I knew that the generation itself can be done in a single SQL query (although it was gonna be a fat one). 

So instead of choosing a serverless document DB I wanted a standard relational DB and specifically Postgres. But I didn't want the hustle of hosting and managing it. Then I discovered [Neon](https:\\neon.tech).

## Neon, a serverless Postgres
> The fully managed multi-cloud Postgres with a generous free tier. We separated storage and compute to offer autoscaling, branching, and bottomless storage.
> - neon.tech

Serverless connotes effortless deploy, scaling and availability. Serverless functions are quite well known concept now. You probably know the Firebase implementation or AWS lambda functions. Basically it's a piece of code that you don't have to host, monitor, manage... etc. yourself. You write it, ship it and it just works. If it doesn't get traffic, it automatically scales down or completely turns itself off. On the other hand on the occasion of a sudden surge of requests the functions gets more resources allocated automatically and your business continues to make you rich.

Ok so imagine having a database that scales automatically and turns itself off when you don't use it. That's Neon. And if you need to add a few extra billions of rows, no problem the storage scales too.

### Branching, a killer feature
Consider how you develop and test changes to the DB, be it the scheme or data migration. You might have a staging environment with some fixtures simulating production DB. You try your change first there then you clench your ass and do the same thing on production. Neon got better solution for that.

At any point of time you can duplicate, branch off, your database. So your new workflow might look like this: create a new branch out of prod. branch (main), run your migrations, test or somehow check that everything went ok, then run the migration on main. Since you've tested your migration on a disposable exact copy of the production DB you can be sure that your change didn't wipe all your business data or whatever hellish scenario you can come up with.

It's similar to how GIT works. So any developer can create their branches and delete them any time. Also it's fast and easy to do so. And now there is a CLI for Neon which makes the workflow easier and can facilitate automation.

*There must be more use cases for this feature but I'm not a DB specialist so you tell me (in the comment section).*

### Still a technical preview but...
Yeah, Neon is still officially in technical preview stage. But the Neon developers basically keep it this way due to their perfectionism. They have a feature list they want to create and until those are done, they won't officially kick the product off. But the main things are done and they work well. Meaning the database itself, scaling and branching.

I've encountered problems with the SQL editor on the Neon dashboard. (The web dashboard overall has this *beta* feeling to it.) The editor throws syntax errors on me but when I run my scripts in a DB admin on my machine, it works. And as of now there is no feature that would let you gather logs in some useful way, which can be a bummer for many users.

## Postgres.js, I choose you (and not an ORM)
Let's use the Neon DB in a Node and specifically Nest.js app.

I don't like to work with ORMs. I'd rather separate the DB from my backend because I'm concerned with separation of different system layers. I consider it a bad practice when data mixes with logic of the system. Coupling them makes it way harder to change anything, more prone to bugs and from a certain size of the project impossible to change or certain decisions.

On top of that I'd rather write SQL then use some kind of builder. I feel like this kind of abstraction is not very helpful. But rawdogging SQL as string is bound to introduce bugs to your code. So I think that library like [Postgres.js](https://github.com/porsager/postgres) is a perfect solution. It makes use of JS template strings and checks that your queries make sense. Yes you can still make a typo in a field or table name but that can be solved easily by your IDE. For example I use WebStorm as a DB admin tool and when I have the the DB introspected I get code suggestions when writing SQL.

There are some quirks you need to get used to when using this library and yes it's also a kind of abstraction especially when nesting SQL expressions but it resembles the SQL more then any builder while still keeping you safe.

### Implementation in a Nest.js app
Let's get coding! When creating a DB and a branch in Neon you get connection details. Save these details to the `.env` file and let's build a simple DB service which we can use throughout our application.
```
# Neon postgres connection  
PGHOST="..."  
PGDATABASE="..."  
PGUSER="..."  
PGPASSWORD="..."  
ENDPOINT_ID="..."
```

```TypeScript
import { ConfigService } from '@nestjs/config';  
import { Injectable } from '@nestjs/common';  
import * as postgres from 'postgres';

@Injectable()  
export class DbService {  
	constructor(private configService: ConfigService) {}  // 1
	  
	private PG_HOST = this.configService.get<string>('PGHOST');  // 2
	private PG_DATABASE = this.configService.get<string>('PGDATABASE');  
	private PG_USER = this.configService.get<string>('PGUSER');  
	private PG_PASSWORD = this.configService.get<string>('PGPASSWORD');  
	private ENDPOINT_ID = this.configService.get<string>('ENDPOINT_ID');  
	  
	private readonly URL = `postgres://username:password@host/database?options=project%3D${this.ENDPOINT_ID}`;  // 3
	  
	readonly sql = postgres(this.URL, {  // 4
	username: this.PG_USER,  
	password: this.PG_PASSWORD,  
	host: this.PG_HOST,  
	database: this.PG_DATABASE,  
	ssl: 'require',  
	});  
}
```

1. First we grab the Nest ConfigService which gives us access to the environmental variables
2. We extract them. (Notice that validation is missing here, so if I forget to provide `.env` file the app crashes, don't do that)
3. Here we prepare the URL string
4. The Postgres.js gets the URL string we've prepared, fills in the variables in place of the keywords like `username` and returns the `postgres.Sql` method. (Notice that the `ENDPOINT_ID` is not one of the predefined aka standard Postgres connection elements so I've just baked it in the string using template string)

Since my app is built using the Nest.js framework I make use of the dependency injection which is a big part of the framework. So this service can be registered as a provider in any Nest.js module. Like so:

```TypeScript
@Module({
	imports: [ConfigModule],
	exports: [...],
	providers: [DbService, GetUsersPgOperation],
})
export class InfrastructureModule {}
```

The ConfigModule from Nest must be accessible to our service in order to reach the environmental variables.

Finally let's use the service to get a list of users.
```TypeScript
export class GetUsersPgOperation {  
	constructor(  
		@Inject(DbService)  // 1
		private db: DbService,  
	) {}  
	  
	async execute(): Promise<User[]> {  
		try {  
			const result = await this.db.sql<UserInterface[]>`select * from users_table`;  // 2
			  
			if (!result) {  
				// handle this  
			}  
			  
			return result.map(...)  
		} catch (error) {  
			// handle error
		}  
	}  
}
```

1. Grab the service
2. Call the `sql` method, provide return type and the query itself. (Return type must be an array because it represents the rows which our DB will return)

That's it. We have a reliable, serverless Postgres DB available to our application!

*Thanks for reading and please let me know what you think about Neon, my implementation or how horribly wrong I'm about ORM in the comment section.*