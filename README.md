----------------------------------------------------------------------------------------------------------------
Title: The Facade Pattern

Sources:
Notes below regarding facade pattern taken from "Design Patterns - Elements of Reusable Object-Oriented Software"
By Gamma, Helm, Johnson, Vlissides

Example Code provided by Derek Banas:
Tutorial: https://www.youtube.com/watch?v=B1Y8fcYrz5o
Source Code: http://www.newthinktank.com/2012/09/facade-design-pattern-tutorial/

Author: Justin J

Purpose: FAU Object Oriented Software Design Course, Sprint 2017

----------------------------------------------------------------------------------------------------------------

Intent
- provide a unified interface to a set of interfaces in a subsystem
- facade defines higher level interface that makes subsystem easier to use

Motivation
- reduces complexity
- minimize communication and dependencies between subsystems
- facade object provides single simplified interface to the more general facilities of subsystem

Applicability
- to provide simple interface to complex subsystem, simple default view of subsystem that is good enough for most clients
- when there are many dependencies between clients and the implementation classes of an abstraction, to decouple the subsystem
- to layer subsystem, the facade defines entry point to each layer
  
Structure
- see facademodel.png

Participants
- facade
	- knows which subsystem classes are responsible for a request
	- delegates client requests to appropriate subsystem objects
- subsystem classes
	- implement subsystem functionality
	- handle work assigned by facade object
	- have no knowledge of the facade, keeps no references to it

Collaborations
- clients communicate with subsystem by sending requests to facade, which then forwards them to approrpiate subsystem objects
- clients that use facade don't have to access its subsystem objects directly

Consequences
- shields clients from subsystem components, reducing number of objects that clients deal with
- promotes weak coupling between the subsystem and its clients
	- weak coupling lets you vary components of subsystem without affecting clients
	- reducing compilation dependencies is vital in large software systems
- it doesn't prevent applications from using subsystem classes if they need to, client can choose
	  
Implementation
- reducing client subsystem coupling
	- coupling between clients and subsystem can be reduced further by making facade an abstract class with conrete subclassses
	- clients can communicate with subsystem through the interface of abstract facade class
	- abstract coupling keeps clients from knowing which implementation of subsystem is used
	- alternatively, configure facade object with different subsystem objects. Customizing facade requires replacing subsystem objects
- public versus private subsystem classes
	- public interface to subsystem consists of classes that all clients can access, where private interface is is just for
	  subsystem extenders
	- making subsystem classes private would be useful, but few object orientated langauges support it
 
Related Patterns
- abstract factory, mediator
- often implemented as a Singleton
 

          	