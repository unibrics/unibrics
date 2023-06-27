# Unibrics
![GitHub](https://img.shields.io/github/license/unibrics/unibrics?style=for-the-badge&color=blue)

#### What is Unibrics?

Unibrics is an open source framework for game development in Unity focused on two main tasks:
1. Provide an [architectural basis](https://github.com/unibrics/unibrics.core) for designing modular, extendable, and configurable applications.
2. Provide a set of optional modules for solving common tasks in game development, such as:
- [modular saves](https://github.com/unibrics/unibrics.saves);
- [configuration and AB-tests](https://github.com/unibrics/unibrics.configuration);
- analytics
and more.


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
1. Create a new Unity project (or open an existing one).
2. At the moment, the installation of Unibrics packages is only possible through the use of the git link, so open your `Packages/manifest.json` file and add the following dependencies:
   ```
    "com.unity.test-framework": "1.1.33",
    "unibrics.core": "git@github.com:unibrics/unibrics.core.git#v0.1.14",
    "unibrics.di.extenject": "git@github.com:unibrics/unibrics.di.extenject.git#v0.1.4",
   ```
   Unibrics packages contain Test assemblies, so we need to add a dependency on the test framework from Unity. Besides that, we're adding link to Core project (with abstract DI interfaces) and package with default DI implementation, which is Extenject in our case.
> **Note**
> After Extenject was merged back to the main Zenject repository latest versions of Zenject are not available to install via git or openUPM. Currently we're keeping dependency on Extenject library to keep installation simple and transparent
3. Add block with custom openUPM scope to your `manifest.json. We're adding Extenject and NSubstitute (used in test assemblies) libraries from [OpenUPM](https://openupm.com/) - Open Source Unity Package Registry:
  ```
  "scopedRegistries": [
    {
      "name": "package.openupm.com",
      "url": "https://package.openupm.com",
      "scopes": [
        "com.svermeulen.extenject",
        "net.tnrd.nsubstitute"
      ]
    }
  ]
  ```
4. 95% of the time you will not need to interact directly with DI framework (Extenject in our case), but you need to perform an initial setup:
   - Create a gameobject, call it ProjectContext;
   - Add a child gameobject, call it AppInstaller and add an AppInstaller script from Unibrics.Core library;
   - Add link to AppInstaller to Mono Installers field in ProjectContext;
   - Drag and drop ProjectContext to Resources folder (it must be root, subfolders will not work);
4. Now, basic setup is done and we're finally ready to start writing our code! So, return to Unity and create your first assembly. Active use of different assemblies for different features is one of the most important concepts used in Unibrics and you will not be able to use it with single assembly per project.
5. Add a reference to Unibrics Core assembly. All your future modules will have that dependency. You don't need to (even more, you shouldn't) add links to `Di.Extenject` or `Extenject` libraries - DI is covered in Core repository
6. Put first files to your assemble - let's create a sample interface and sample implementation of it.
   ```C#
   namespace Sample.App
   {
       using UnityEngine;

       public interface ISampleInterface
       {
           void SayHello();
       }

       class SampleImplementation : ISampleInterface
       {
           public void SayHello()
           {
               Debug.Log($"Hello from Unibrics!");
           }
       }
   }
   ```
8. Create module installer
9. Add AssemblyInfo.cs
10. Add inject to monobeh
11. Start an application
