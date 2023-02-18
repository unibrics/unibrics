# Unibrics
![GitHub](https://img.shields.io/github/license/unibrics/unibrics?style=for-the-badge&color=blue)

#### What is Unibrics?

Unibrics is an open source framework for game development in Unity focused on two main tasks:
1. Provide an architectural basis for designing modular, extendable, and configurable applications.
2. Provide a set of optional modules for solving common tasks in game development, such as modular saves, AB-tests, configuration, analytics, and more.


## Why do we need that?
Unity is a mainstream game engine with the biggest market share since the early 2010s, absolute majority of mobile games are made with it. But developers community still struggles with architectural problems and lack of libraries to speed up the development of common parts for every game. 

For example, in back-end development, engineers usually work with well established and mature instruments such as ASP.NET or [Spring](https://spring.io/quickstart). These frameworks provide developers a lot of benefits, including:
- An architectural framework is provided for writing code, organizing it in projects, and performing common tasks.
- A straightforward method for dealing with dependencies in code via DI;
- Many common tasks (authorization, logging, configuration, etc.) have already been implemented (with thousands of hours invested) and are included in the framework itself and accessible via a clear API.
- Developers can focus on business logic;
- Good documentation and large developers community to get knowledge from.

As a result, an engineer who is starting his career in this field is very limited in ways to do something completely wrong or to come with poor solution for some common task like authentication. Framework as an environment provides good practices to follow and bad practices to avoid.

In Unity, on the other hand:
- Almost every game is written from scratch; you may use Asset Store assets from various developers, which are frequently difficult to combine;
- Poor engineering practices such as extensive use of singletons, writing everything in one huge DLL, high coupling are often seen in even big projects; 
- Every team repeatedly implements standard parts for every game, such as configuration, saving systems, analytics, and tutorials.

**Unibrics** is an attempt to create an example of a framework for Unity development that can fix some of these problems by implementing best practices from other fields of software engineering and bringing them to game development.

## So, how can we use it?

Unibrics can be used on different levels:
1. You can just take it as an example on how to design your application in modular, framework-agnostic way according to Open-Closed Principle.
2. You can import it's Core and use it to separate Dependency Injection API from implementation and to build your own modules.
3. You can use some (or even all) modules to implement needed functionality, such as saves system and focus on your business logic.

## Unibrics Architecture

## Quick start
