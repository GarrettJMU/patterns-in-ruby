
# Design Patterns

## Creational Patterns
-   ## Abstract Factory
    -   ### What is is used for:
	    -   Offers the interface for creating a family of related objects, without explicitly specifying their classes
    -   ### Participants
	    - AbstractFactory
		    - Declares an interface for operations that create abstract products
		- ConcreteFactory
			- Implements operations to create concrete products
	    -  AbstractProduct
		    - Declares an interface for a type of product object
		- Product
			- Defines a product to be created by the corresponding ConcreteFactory; it implements the AbstractProduct interface
		- Client
			- Uses the interfaces declared by the AbstractFactory and AbstractProduct classes
    
    -   ### Pros
		-   You can be sure that the products you’re getting from a factory are compatible with each other
		-   You avoid tight coupling between concrete products and client code
		-   Single Responsibility Principle - you can extract the product creation code into one place, making the code easier to support
		-   Open/Closed Principle - You can introduce new variants of products without breaking existing client code
    -   ### Cons    
	    - The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern

-   ## Builder Factory
    -   ### What is is used for:
	    -   Defines an instance for creating an object but letting subclasses decide which class to instantiate
	    - 
    -   ### Participants
	    - Builder
		    - Specifies an abstract interface for creating parts of a Product object
		- ConcreteBuilder  
			- Constructs and puts together parts of the product by implementing the Builder interface. It defines and keeps track of the representation. It creates and provides an interface for saving the product  
	    -  Director
		    - Class constructs the complex object using the Builder interface  
		- Product
			- Represents the complex object that is being built  
    -   ### Pros
		-   You can construct objects step by step, defer construction steps or run steps recursively  
		- You can reuse the same construction code when building various representations of products  
		- Single Responsibility Principle - You can isolate complex construction code from the business logic of the product  
    -   ### Cons    
	    - Overall complexity of the code increases since the pattern requires creating multiple new classes
## Structural Patterns
## Behavioral Patterns


 ### Observer
    
#### What is it used for
- Defines a one to many dependency between objects so that when one object changes state, all of its dependents are notified and updated automatically
-    Change of state must be reflected in another object without tight coupling
-   Framework we are writing needs to be enhanced in future with new observers with minimal changes
-   MVC pattern is used to decouple the model from the view.
	-   In this scenario the View is the observer and the model is the observable

### Participants
    

-   #### Observable
    

	-   Interface or abstract class defining the operations for attaching and detaching observers to the client. In the FOG book this class/interface is known as Subject
    

-   ConcreteObservable
    

-   Concerte Observable class. It maintains the state of the object and when a change in the state occurs it notifies the attached Observers
    

-   Observer
    

-   Interface or abstract class defining the operations to be used to notify this object
    

-   ConcreteObserverA, ConcreteObserver2
    

-   ConcreteObserver implementations
    

-   Pros:
    

-   Supports notion of loosely coupled item
    
-   Efficient way of sending data to multiple “observers”
    
-   You can add and remove as needed
    

-   Cons:
    

-   Can create unnecessary complexity
    
-   Order of dependable notifications is not always in order
    

-   ## Interpreter
    

-   What is is used for:
    

-   A way for unrecognized information to be put into a coherent manner
    
-   Grammar and light math interpretation
    

-   Participants
    

-   AbstractExpression
    

-   Declares an interpret() operation that all nodes (terminal and nonterminal) in the AST overrides
    

-   TerminalExpression
    

-   Implements the interpret() operation for terminal expressions
    

-   NonterminalExpression
    

-   Implements the interpret operation for all nonterminal expressions
    

-   Context
    

-   Contains information that is global to the interpreter. It is this string expression with the postfix notation that has to be interpreted and parsed
    

-   Client
    

-   Builds (or is provided) the AST assembled from TerminalExpression and NonterminalExpression. The Client invokes the interpret() operation
    

-   Pros:
    

-   Easy to add and move things in interpretation
    
-   Implementing grammar is too easy
    

-   Cons:
    

-   Complex grammar is hard to handle
    

-   ## Command
    

-   What is is used for:
    

-   Encapsulate request in single object
    
-   Allow parameterization of requests from clients
    
-   Allow saving into a queue
    

-   Participants
    

-   Command
    

-   Declares interface for executing an operation
    

-   ConcreteCommand
    

-   Extends the COmmand interface, implementing the execute method by invoking the corresponding operations on Receiver. It defines a link between the Receiver and the action
    

-   Client
    

-   Creates a ConcreteCommand object and sets its receiver
    

-   Invoker
    

-   Asks the command to carry out the request
    

-   Receiver
    

-   Knows how to perform the operations
    

-   Pros:
    

-   Decouples objects
    
-   Add new command without changing existing code
    
-   Can create a sequence of commands (macro). Create a list of Command instances and call the execute method of all commands
    
-   Undo/Redo easily
    

-   Cons:
    

-   Increase in number of classes for each command
    

-   ## Memento
    

-   What is is used for:
    

-   Capture the internal state of an object without violating encapsulation and thus providing a mean for restoring the object into initial state when needed
    

-   Participants
    

-   Caretaker
    

-   Responsible for keeping memento
    
-   Caretaker knows nothing of memento
    
-   Caretaker must not operate on it
    

-   Memento
    

-   Stores internal state of Originator. The state can include any number of state variables
    
-   Memento must have two interfaces, an interface to the caretaker. This interface must not allow any operations or any access to internal state stored by the memento and thus honors encapsulation.
    
-   The other interface is to the originator and allows the originator to access any state variables necessary for the originator to restore previous state
    

-   Originator
    

-   Creates a memento object capturing the originators internal state
    
-   Use the memento object to restore its previous state
    

-   Pros:
    

-   You can produce snapshots of the object's state without violating the encapsulation
    
-   You can simplify the originators code by letting the caretaker maintain the history of the originators state
    

-   Cons:
    

-   If clients create mementos often it’ll kill RAM usage
    
-   Caretakers should track the originator’s lifecycle to be able to destroy obsolete mementos
    
-   Most dynamic programming languages can’t guarantee that the state within the memento stays untouched
    

-   ## State
    

-   What is is used for:
    

-   Behavioral pattern that allows an object to alter its behavior when its internal state changes. It appears as if the object changed it’s class
    

-   Participants
    

-   Context
    

-   Defines the interface of interest to clients and maintains an instance of a ConcreteState subclass that defines the current state
    

-   State
    

-   Defines an interface for encapsulating the behavior associated with a particular state of the Context
    

-   ConcreteState
    

-   Each subclass implements a behavior associated with a state of the Context
    

-   Pros:
    

-   Single Responsibility Principle - organizes the code related to particular states into separate classes
    
-   Open/Closed Principle - Introduces new states without changing existing state classes or the context
    
-   Simplify the code of the context by eliminating bulky state machine conditionals
    

-   Cons:
    

-   Applying this pattern can be overkill if a state machine has only a few states or rarely changes
    

-   ## Strategy
    

-   What is is used for:
    

-   Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it
    
-   Context class takes in a ConcreteStrategy class
    

-   Participants
    

-   Strategy
    

-   Defines an interface common to all supported algorithms. Context uses this interface to call the algorithm defined by a ConcreteStrategy
    

-   ConcreteStrategy
    

-   Each concrete strategy implements an algorithm
    

-   Context
    

-   Contains a reference to a strategy object
    
-   May define an interface that lets strategy accessing its data
    

-   Pros:
    

-   Change to better name
    
-   Change function declaration, rename variable or rename field refactoring seem appropriate
    

-   Cons:
    

-   Creating a name that noone understands
    

-   ## Composite
    

-   What is is used for:
    

-   Intent of this pattern is to compose objects into tree structures to represent part-whole hierarchies
    
-   Composite lets clients treat individual objects and compositions of objects uniformly
    

-   Participants
    

-   Component
    

-   Component is the bastraction for leafs and composites. It defines the interface that must be implemented by the objects in the composition. For example a file system resource defines move, copy, rename, and getSize methods for files and folders
    

-   Leaf
    

-   Leafs are objects that have no children. They implements services described by the COmponent interface. For example a file object implementes move, copy, rename, as well as getSize methods which are related to the Component interface
    

-   Composite
    

-   A composite stores child components in addition to implementing methods defined by the component interface. Compsoties implement methods defined in the Component interface by delegating to child components. In addition composites provide additional methods for adding, removing, as well as getting components
    

-   Client
    

-   Client manipulates objects in the hierarchy using the component interface
    

-   Pros:
    

-   You can work with complex tree structures more conveniently: use polymorphism and recursion to your advantage
    
-   Open/Closed Principle - You can introduce new element types into the app without breaking the existing code, which now works with the object tree
    

-   Cons:
    

-   It might be difficult to provide a common interface for classes whose functionality differs too much. In certain scenarios, you’d need to overgeneralize the component interface, making it harder to comprehend
    

-   ## Template Method
    

-   What is is used for:
    

-   Define the skeleton of an algorithm in an operation, deferring some steps to subclasses
    
-   Template lets subclasses redefine certain steps of an algorithm without letting them change the algorithms structure
    

-   Participants
    

-   AbstractClass
    

-   Defines abstract primitive operations that concrete subclasses define to implement steps of an algorithm.
    
-   Implements a template method which defines the skeleton of an algorithm. The template method calls primitive operations as well as operations defined in AbstractClass or those of other objects
    

-   ConcreteClass
    

-   Implements the primitive operations to carry out subclass-specific steps of the algorithm
    
-   When a concrete class is called the template method code will be executed from the base class while for each method used inside the template method will be called the implementation from the derived class
    

-   Pros:
    

-   You can let clients override only certain parts of a large algorithm, making them less affected by changes that happen to other parts of the algorithm
    
-   You can pull the duplicate code into a superclass
    

-   Cons:
    

-   Some clients may be limited by the provided skeleton of an algorithm
    
-   You might violate the Liskov Substitution Principle by suppressing a default step implementation via a subclass
    
-   Template methods tend to be harder to maintain the more steps they have
    

-     
    

-   ## Factory Method
    

-   What is is used for:
    

-   Defines an interface for creating objects, but let subclasses decide which class to instantiate
    
-   Refers to the newly created object through a common interface
    

-   Participants
    

-   Product
    

-   Defines the interface for objects the factory method creates
    

-   ConcreteProduct
    

-   Implements the Product interface
    

-   Creator
    

-   Also referred as Factory because it creates the Product objects
    
-   Declares the method FactoryMethod, which returns a Product object.
    
-   May call the generating method for creating Product objects
    

-   ConcreteCreator
    

-   Overrides the generating method for creating COncreteProduct objects
    

-   Pros:
    

-   You avoid tight coupling between the creator and the concrete products
    
-   Single Responsibility Principle - you can move the product creation code into one place in the program, making the code easier to support
    
-   Open/Closed Principle - You can introduce new types of products into the program without breaking existing client code
    

-   Cons:
    

-   The code may become more complicated since you need to introduce a lot of new subclasses to implement the patter. The best case scenario is when you’re introducing the pattern into an existing hierarchy of creator classes
    

-     
    

-   ## Abstract Factory
    

-   What is is used for:
    

-   Offers the interface for creating a family of related objects, without explicitly specifying their classes
    

-   Participants
    

-   AbstractFactory
    

-   Declares an interface for operations that create abstract products
    

-   ConcreteFactory
    

-   Implements operations to create concrete products
    

-   AbstractProduct
    

-   Declares an interface for a type of product object
    

-   Product
    

-   Defines a product to be created by the corresponding ConcreteFactory; it implements the AbstractProduct interface
    

-   Client
    

-   Uses the interfaces declared by the AbstractFactory and AbstractProduct classes
    

-   Pros:
    

-   You can be sure that the products you’re getting from a factory are compatible with each other
    
-   You avoid tight coupling between concrete products and client code
    
-   Single Responsibility Principle - you can extract the product creation code into one place, making the code easier to support
    
-   Open/Closed Principle - You can introduce new variants of products without breaking existing client code
    

-   Cons:
    

-   The code may become more complicated than it should be, since a lot of new interfaces and classes are introduced along with the pattern
    

-   ## Singleton
    

-   What is is used for:
    

-   Ensure that only one instance of a class is created
    
-   Provide a global point of access to the object
    

-   Participants
    

-   Singleton class
    

-   Involves one constructor and a static public method that returns a reference to the static member
    

-   Pros:
    

-   You can be sure that a class has only a single instance
    
-   You gain a global access point to that instance
    
-   Singleton object is initialized only when it’s requested for the first time
    

-   Cons:
    

-   Violates the single responsibility principle - the pattern solves two problems at the time
    
-   Can mask bad design, for instance, when the components of the program know too much about each other
    
-   Requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times
    
-   May be difficult to unit test the client code of the singleton because many test frameworks rely on inheritance when producing mock objects. Since the constructor of the singleton class is private and overriding static methods are impossible in most languages, you will need to think of a creative way to mock the singleton. Or just don’t write tests… or don’t use singleton pattern
    

-   ## Adapter
    

-   What is is used for:
    

-   Convert the interface of a class into another interface clients expect
    
-   Adapter lets classes work together, that could not otherwise because of incompatible interfaces
    

-   Participants
    

-   Target
    

-   Defines the domain-specfic interface that Client uses
    

-   Adapter
    

-   Adapts the interface adaptee to the target interface
    

-   Adaptee
    

-   Defines an existing interface that needs adapting
    

-   Client
    

-   Collaborates with objects conforming to the Target interface
    

-   Pros:
    

-   Single Responsibility Principle - you can separate the interface or data conversion code from the primary business logic of the program
    
-   Open/Closed Principle - you can introduce new types of adapters into the program without breaking the existing client code, as long as they work with the adapters through the client interface
    

-   Cons:
    

-   Overall complexity of the code increases because you need to introduce a set of new interfaces and classes.
    
-   Sometimes it’s simpler just to change the service class so that it matches the rest of your code
    

-   ## Decorator
    

-   What is is used for:
    

-   Add additional responsibilities dynamically to an object
    

-   Participants
    

-   Component
    

-   Interface for objects that can have responsibilities added to them dynamically
    

-   ConcreteComponent
    

-   Defines an object to which additional responsibilities can be added
    

-   Decorator
    

-   Maintains a reference to a Component object and defines an interface that conforms to Component’s interface
    

-   Concrete Decorators
    

-   Concrete Decorators extend the functionality of the component by adding state or adding behavior
    

-   Pros:
    

-   You can extend an objects behavior without making a new subclass
    
-   You can add or remove responsibilities from an object at runtime
    
-   You can combine several behaviors by wrapping an object into multiple decorators
    
-   Single Responsibility Principle - you can divide a monolithic class that implements many possible variants of behavior into several smaller classes
    

-   Cons:
    

-   Hard to remove a specific wrapper from the wrappers stack
    
-   Hard to implement a decorator in such a way that its behavior doesn’t depend on the order in the decorators stack
    
-   Initial configuration code of layers might look ugly
    

-   ## Chain of Responsibility
    

-   What is is used for:
    

-   Avoids attaching the sender of a request to its receiver, giving this way other objects the possibility of handling the request too
    
-   Objects become parts of a chain and the request is sent from one object to another across the chain until one of the objects will handle it
    

-   Participants
    

-   Handler
    

-   Defines an interface for handling requests
    

-   RequestHandler
    

-   Handles the requests it is responsible for
    
-   If it can handle the request it does so, otherwise it sends the request to its successor
    

-   Client
    

-   Sends commands to the first object in the chain that may handle the command
    

-   Pros:
    

-   You can control the order of request handling
    
-   Single Responsibility Principle - you can decouple classes that invoke operations from classes that perform operations
    
-   Open/Closed Principle - you can introduce new handlers into the app without breaking the existing client code
    

-   Cons:
    

-   Some requests may end up unhandled
    

-     
    

-   ## Proxy
    

-   What is is used for:
    

-   Intent is to provide a placeholder for an object to control references to it
    

-   Participants
    

-   Subject
    

-   Interface implemented by the RealSubject and representing its services. The interface must be implemented by the proxy as well so that the proxy can be used in any location where the RealSubject can be used
    

-   Proxy
    

-   Maintains a reference that allows the Proxy to access the RealSubject
    
-   Implements the same interface implemented by the RealSubject so that the Proxy can be substituted for the RealSUbject
    
-   Controls access to the RealSubject and may be responsible for its creation and deletion
    
-   Other responsibilities depend on the kind of proxy
    

-   RealSubject
    

-   Real object that the proxy represents
    

-   Pros:
    

-   You can control the service object without clients knowing about it
    
-   You can manage the lifecycle of the service object when clients don’t care about it
    
-   Proxy works even if the service object isn’t ready or is not available
    
-   Open/Closed Principle - you can introduce new proxies without changing the service or clients
    

-   Cons:
    

-   Code may become more complicated since you need to introduce a lot of new classes
    
-   Response from the service might get delayed
    

-   ## Bridge
    

-   What is is used for:
    

-   Intent of this pattern is to decouple abstraction from implementation so that the two can vary independently
    

-   Participants
    

-   Abstraction
    

-   Abstraction defines abstraction interface
    

-   AbstractionImpl
    

-   Implements the abstraction interface using a reference to an object of type Implementor
    

-   Implementor
    

-   Defines the interface for implementation classes
    
-   This interface does not need to correspond directly to abstraction interface and can be very different
    
-   Abstraction imp provides an implementation in terms of operations provided by Implementor interface
    

-   ConcreteImplementor1, ConcreteImplementor2
    

-   Implements the implementor interface
    

-   Pros:
    

-   Create platform-independent classes and apps
    
-   Client code works with high level abstractions. It isn’t exposed to the platform details
    
-   Open/Closed Principle - You can introduce new abstractions and implementations independently from each other
    
-   Single Responsibility Principle - You can focus on high-level logic in the abstraction and on platform details in the implementation
    

-   Cons:
    

-   Might make the code more complicated by applying the pattern to a highly cohesive class
    

-   ## Builder
    

-   What is is used for:
    

-   Defines an instance for creating an object but letting subclasses decide which class to instantiate
    
-   Refers to the newly created object through a common interface
    

-   Participants
    

-   Builder
    

-   Specifies an abstract interface for creating parts of a Product object
    

-   ConcreteBuilder
    

-   Constructs and puts together parts of the product by implementing the Builder interface. It defines and keeps track of the representation. It creates and provides an interface for saving the product
    

-   Director
    

-   Class constructs the complex object using the Builder interface
    

-   Product
    

-   Represents the complex object that is being built
    

-   Pros:
    

-   You can construct objects step by step, defer construction steps or run steps recursively
    
-   You can reuse the same construction code when building various representations of products
    
-   Single Responsibility Principle - You can isolate complex construction code from the business logic of the product
    

-   Cons:
    

-   Overall complexity of the code increases since the pattern requires creating multiple new classes
