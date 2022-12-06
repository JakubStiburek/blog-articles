---
tags:
  - Rust
  - en
---
# The Beginning

## 13. 2. 2022

Today marks the first time ever I have written a Rust code. I have followed “the book”, the official handbook for the Rust language ([here it is](https://doc.rust-lang.org/book/)) , and have written two programs: Hello world and Guess the Number Game.

How have I learned about Rust. I’m actually a web developer and I usually work with JavaScript or TypeScript on front-end. So I develop web UI. I have no CS degree and all the official education in CS I have constists of what they have thought me in high school, which wasn’t much since it was only an electrical engineering school. I’m from Europe and high schools work quite different from those in US here, the high schools here center around a certain goal: e.g. go to University, professional aim etc. I have learned web development on my own and felt pretty acomplished when I’ve succesfully started a career in programming.

Nevertheless I’m at the point now where I feel like what I’m doing isn’t enough. I’m not really sure what I want but I feel like I should try to make something different than another web app or website. So I have investigated what other languages or technologies I might be interested in. And suddenly my favourite YT channel, which focuses on 100 second long (more like 100 sec short) videos explaining various programming topics, published a video about the Rust programming language. And I felt like - wow this is it.

What is it actually that got me so much interested in the language on the first brief sight? I have no idea. But I know that I want to understand it and that’s the only driving force necessary for starting a new learning journey.

So it begins. And I wonder where will this journey get me.

### Learning in public

I’m planning on trying the technique of learning in public. Many people online recommend doing it. It supposedely should make me not quit and by trying to explain things make myself understand them better. The second thing I know for sure works because I have worked as a language teacher before, the first thing... we will see. Anyway if you want to follow my journey, I’ll be posting updates here and later on my personal website (that one is under reconstruction at the moment so I’ll share it with you when it’s done).

### Goals

I believe that I should have a certain goal or goals in front of me so that I know how far I’m in the progress and what lies in front of me. I’ll try to make up a few points that I feel like are acomplishable in the near future.

-   [ ] learn the basic syntax
    -   quite self-explenatory I believe
-   [ ] make a simple CLI program
    -   I’ve got the recommendation from another YT person that CLI is a good starting point and I could actually make something really useful to me right from the beginning
    -   I’m thinking of currency rate calculater or something of that sort
-   [ ] learn about connecting to the web
    -   I want to know, eventualy, how to make a REST api, because that’s again something I could really use, e.g. creating a backend for my personal website
-   [ ] make a simple REST api
    -   by simple I mean one endpoint or something like that
    -   maybe I could make the CLI program I would have done by this time accesible on the www
-   [ ] make new goals
    -   I know already that it would take me at least a few months before I get here, so nothing further needs to be planned, when I get here I’ll figure out some proper project

### Conclusion

I have started to learn a new programming lanaguage. I hope it will be a lot of fun and I’ll get to create amazing things with it and I want to try to do it in public. If you feel like you wanted to start something new lately, join me and learn with me. We can move each other forward.

---

The book: [](https://doc.rust-lang.org/book/)[https://doc.rust-lang.org/book/](https://doc.rust-lang.org/book/)

The 100 sec channel: [](https://www.youtube.com/c/Fireship)[https://www.youtube.com/c/Fireship](https://www.youtube.com/c/Fireship)

The Let’s get rusty channel: [](https://www.youtube.com/channel/UCSp-OaMpsO8K0KkOqyBl7_w)[https://www.youtube.com/channel/UCSp-OaMpsO8K0KkOqyBl7_w](https://www.youtube.com/channel/UCSp-OaMpsO8K0KkOqyBl7_w)

My GitHub where I’ll store my Rust projects: [](https://github.com/JakubStiburek)[https://github.com/JakubStiburek](https://github.com/JakubStiburek)

## 14. 2. 2022

### Variables and mutability

So in Rust we can declare variables by using the `let` or `const` keyword. `let` can be also followed by `mut` .

Variables are in Rust immutable by default, so once you declare a variable it keeps its content unchanged. This behaviour can be overridden using the `mut` keyword. That makes a variable mutable. See below some code for ilustration.

```rust
// this will result in error
let a = 45;
a = 55;

~~~~// this is a ok
~~~~let mut a = 45;
a = 55;
```

Variables are tied to the scope they were declared in.

```rust
fn main() {
    let a = 45;

    {
        // this is another scope
        let a = 55;
        println!("a in another scope is: {}", a);
    }

		 println!("a is: {}", a);
}

// a in another scope is 55
// a is 45
```

_Shadowing_ is a Rust feature that allows you to use a variable name twice.

```rust
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {}", x);
    }

    println!("The value of x is: {}", x);
}
```

The x is first introduced as an integer of value 5, then “redeclared” as “5 + 1”. The second declaration _shadows_ the original one. From this point in the code x is equal to 6. Later in the lower scope the x is again shadowed and effectively a new variable x is declared. But this one lives only in the current so scope. So the print statement at the end of the snippet will yield 6 and the one within the lower scope will get us 12.

This is different from `mut` because this way we can change the type of a variable.

```rust
fn main() {
    let x = "   "; // String

    let x = x.len(); // Integer

		let mut x = "   ";

		x = x.len() 
		// this will result in an error because x is a String 
		// and cant't be assigned an Integer
}
```

Constants are variables that can contain only a constant expression, not the result of a value that could only be computed at runtime, they are immutable and cannot be made mutable by the `mut` keyword and they must be type annotated. Also the convention is to type them in all caps using underscores in between words.

Constants are basically variables that you can be sure that they won’t change. This makes them perfect for storing some global data.

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```