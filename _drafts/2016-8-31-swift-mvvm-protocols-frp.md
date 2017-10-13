---
layout: post
title: Bringing Together MVVM, Functional Reactive Programming, and Protocols in Swift
permalink: /swift-mvvm-frp-protocols
excerpt: Nowadays, the Swift developer has a mind-bending number of things to consider when architecting an application. Where Objective-C was aggressively object-oriented, Swift is relatively accommodating to a number of different styles without enforcing certain patterns. The downside to this, of course, is that it is up to the developer to understand the different approaches to architecture. Lately, MVVM, FRP, and Protocols have been getting a lot of buzz in the Swift community, and for good reason. But for those of us coming from an aggressively object-oriented world, it is difficult to understand each concept, much less use them together. I propose that not only can these things go together, but they were made to go together, and I'm going to talk about how.
---
First, what is MVVM, FRP, and protocol-oriented programming? Let's defer that question for a bit and ask instead: what are the problems that these things are trying to solve?

That is beyond the scope of this post, but here is my crib notes version:

    * MVVM stands for Model-View-View Model, a pattern similar to Model-View-Controller. The View Model sits below the View and is responsible for describing the state of the view in an **abstract** way, without actually implementing the view or dealing with state. The View interacts with the View Model **ONLY**. For more, see this [excellent article](https://artsy.github.io/blog/2015/09/24/mvvm-in-swift/) by Ash Furrow and [this excellent talk](https://realm.io/news/doios-natasha-murashev-protocol-oriented-mvvm/) by Natasha Murashev.
    * FRP stands for Functional Reactive Programming, a general style of programming that *reacts* to asynchronous data/events with *functions*. A common use case for this style is real-time data. With FRP you create a 'stream' to observe changes to some kind of data, and then simply use functional programming to define how to react to those changes. That is a vast oversimplification, but for more, see [this excellent talk](https://realm.io/news/altconf-ash-furrow-functional-reactive-swift/) by Ash Furrow.
    * Protocol Oriented Programming is Apple lingo for favoring the use of protocols to create abstractions (as opposed to, say, subclassing). Protocols are pretty cool and flexible, and if you aren't familiar with them, [here is the canonical talk](https://developer.apple.com/videos/play/wwdc2015/408/) by Dave Abrahams, the tech lead for the Swift standard library.
    
So, that means an app built with these things in mind must have a few important characteristics:

1. MVVM architecture with a fat value type layer, where Views only talk to View Models, and a thin reference type layer where state is managed at the View level only. I'll talk about reference vs. value types a bit more in the next section.
2. FRP at the View Model layer for things that may change over time.
3. Heavy use of protocols for abstractions.

## A Brief Aside on Using Reference and Value Types

When I first started building with Swift, I didn't have any real grasp of the differences between reference and value types, and thankfully, I didn't really need to. Classes in Swift work a lot how you might expect coming from other OOP languages, which was awesome because it meant I could start building things right away. But once I started diving more into the technical details of the language, I realized that I could do sooooo much better. If you're an OOP person and you're getting started with Swift, I would **HIGHLY** recommend you familiarize yourself with reference vs. value types ([this talk by Andy Matuschak](https://realm.io/news/andy-matuschak-controlling-complexity/) made everything click for me).

In Swift, value types are `structs` and reference types are `classes`. The main advantage to using value types is that it greatly simplifies things in your app because you don't have to worry about the side effects of mutable state - all value types are copied on assignment, so you don't get those thorny issues that happen when two different parts of your system mutate one reference. This is kind of a hand-wavy, cop-out definition, but if you don't understand why this is a good thing, watch the talk I linked above until you get it.

The end result is that, in most cases, you should end up with a fat value layer to your app (that doesn't depend on mutable state to make sense), and a thin reference layer whose identity is tied to state (your views). This fits in beautifully with the concepts we're discussing! For MVVM, this means that we handle state at the View layer only, which means that only our View Controllers are classes. Our Models and View Models can be `structs` that simply describe behavior. And Protocols are inherently stateless - they simply describe interfaces between things, and Protocol Extensions can define default implementations and behavior. Our View Models can use FRP to handle the behavior of the UI - all the View must do is send new data and events to the View Model.

## The One Problem with MVVM

... is that it doesn't describe where you would put protocols (and protocol extensions) or other typical controller behavior, such as making a network request. In the Ash Furrow article I linked above he puts this kind of function in the View Model for lack of anywhere better, but I think we can do better.

I propose we talk about another layer that is sorta like the controller in MVC, but with a few key differences. I'll call it the Coordinator layer, for lack of a better term. It sits at the View Model and Model level, and is primarily responsible for defining abstractions and providing stateless behavior, mostly in the form of protocols and (protocol) extensions.

Example: let's say we are building a simple bus tracking app that gets bus locations from an API and displays an icon within a map view for a bus' location. In this app we need a few things: a networking utility to make requests to the API, a Bus model, and a map view to display buses. In MVVM that might look like: `Networking.swift`, `Bus.swift`, `

## Putting it Together

Let's take our example of the bus tracking app and use it to put all this together. Our bus tracking app has a few basic requirements: it needs to display real-time locations for all the buses on the single route in our small town on a map, and it must let us view a list of stops on that route, as well as get directions to that stop. Let's put this into MVVM first.

Our models are pretty straightforward: we have a Bus and a Stop.

Now, for the FRP side - let's start at the top (the views) and work our way down. We'll start with the map view. The map view simply observes its view model's buses array for changes, then updates bus locations whenever those change. That was easy!

For the view models, let's start with the bus map view model. Here, we request
