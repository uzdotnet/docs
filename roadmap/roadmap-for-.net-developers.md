---
description: Mukhammadkarim Tukhtaboev
---

# Roadmap for .NET developers



### Module 0: Introduction to course?

* Who is author?
* About course
* About programming and programming languages

### Module 1: Introduction to .NET and C\#

* What is .NET?
* History of .NET
* Versions of .NET
* Why .NET?
* Major components of .NET
* Installing .NET
* Hello World in 5 minutes and .NET CLI
* Installing IDE (Visual Studio, Rider)
* Introducing project/solution structure

### Module 2: C# Fundamentals

* Print data to console
* Date types and variables
* Input data to console
* String interpolation
* If/else operator
* Switch/case operator
* Goto operator
* Loops, break and continue
* Math functions
* Comments
* Methods and params
* Arrays
* Casting types
* Boxing and unboxing

### Module 3: Essentials C# programming concepts

* Introduction to OOP (vs functional programing)
* Major components of OOP
* Classes and objects
* Constructor and Destructor
* Property and fields
* Incapsulation
* Inheritance and this/base keywords
* Polimorphism
* Abstraction
* Enum and struct
* Value type and reference type
* Ref and out
* String arguments in Main function
* Static, sealed, abstract classes
* String and StringBuilder
* Exception Handling

### Module 4: Advanced topics in .NET

* Collections: IEnumerable, ICollection, IReadonlyList
* Collections: List, Stack, Queue, LinkedList, Dictionary, HashSet, ArrayList
* KeyValuePair, Tuple and ValueTuple
* Delegates
* Events
* Extension methods
* Stream I/O (StreamWriter, StreamReader)
* Stream I/O 2 (FileStream, MemoryStream)
* Using statement
* File and directories
* Multithreading
* Asynchronoues programming
* Reflection and attributes
* HttpClient and HTTP methods

### Module 5: LINQ

* Introduction to LINQ
  1. What is LINQ and why is it important?
  2. Benefits of using LINQ for data querying.
* LINQ query syntax
  1. Basic LINQ query structure.
  2. Using `from`, `where`, `select`, `orderby`, and `groupby` clauses.
  3. Filtering data using `where` clause.
* Projection and transformation
  1. Projecting data using `select` clause.
  2. Working with anonymous types in projections.
  3. Transforming data into different shapes.
* Sorting and grouping
  1. Sorting data using the `orderby` clause.
  2. Grouping data using the `groupby` clause.
  3. Aggregating data within groups.
* Aggregation and aggregation methods
  1. Understanding aggregation functions like `Sum`, `Average`, `Min`, and `Max`.
  2. Using aggregation methods with LINQ queries.
  3. Applying aggregations on grouped data.
* Additional data manipulation methods
  1. Using methods like `All`, `Any`, `Contains`, `Distinct`, `Except`, `Intersect`, `Union`.
  2. Applying these methods in LINQ queries for specific scenarios.
* Paging and filtering methods
  1. Using methods like `Take`, `TakeWhile`, `Skip`, `SkipWhile`.
  2. Applying paging and filtering techniques to query subsets of data.
* Joining data
  1. Using the `Join` method to combine data from multiple sources.
  2. Understanding different types of joins.
* Accessing specific elements
  1. Using methods like `ElementAt`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `SingleOrDefault`.
  2. Retrieving specific elements from a sequence.
* LINQ method syntax
  1. Introduction to LINQ method chaining.
  2. Using methods like `Where`, `Select`, `OrderBy`, `GroupBy`.
  3. Utilizing aggregation and other data manipulation methods.
* LINQ to objects
  1. Querying in-memory collections using LINQ.
  2. Performing various data manipulations using LINQ.
  3. Practicing LINQ with arrays, lists, dictionaries, etc.
* LINQ to XML and JSON
  1. Querying XML and JSON data using LINQ.
  2. Loading and transforming XML/JSON data with LINQ queries.
* Advanced LINQ concepts
  1. Understanding expression trees in LINQ.
  2. Writing custom LINQ extension methods.
  3. Utilizing LINQ for functional-style programming.

### Module 6: Version Control

* Introduction to Version Control
* Setting up git and github
* Basic git commands
* Working with branches
* Remote repositories and Github
* Collaborative development with Pull Requests
* Resolving conflicts
* Advanced git commands
* Git Worklofw strategies
* Git hooks and customization

### Module 7: Database

* What is MS SQL Server?
* Difference editions of SQL Server: Express, Standart, Enterprise
* Installing and setting up MS SQL Server
* Introduction to SQL
* Creating database and tables
* Data types in SQL
* Basic SQL queries: SELECT, INSERT, UPDATE, DELETE
* SELECT statement: Filtering and sorting data
* Working with NULL values
* Aggregation and grouping
* Joins
* Transactions
* Stored Procedure
* Understanding indexes, Clustered, non-clustered and filtered indexes
* Performance tuing: Identifying and improving slow queries
* Working with Views
* Working with Triggers
* Constraints
* Primary and foreign keys
* JSON support in SQL Server
* Backup, Restore and Security
* Users, roles and permissions&#x20;

### Module 8: ORM

* Introduction to ORMs
* Dapper
  1. Introduction to Dapper
  2. Basic CRUD operations
  3. Mapping Data to Objects
  4. Handling Transactions and Stored Procedure
  5. Asynchronous Data Access
  6. Advanced Features and Performance
* Entity Framework Core
  1. Introduction to Entity Framework Core
  2. Setting up data context and entities
  3. Basic CRUD operations with EF Core
  4. Querying data with LINQ and Projections
  5. Relationships and navigation properties
  6. Working with Migrations
  7. Seeding data and data annotations
  8. Advanced querying and filtering
  9. Working with transactions
  10. Performance optimization and caching&#x20;
  11. Code First and Database First approaches

### Module 9: Introduction to ASP.NET Core

* Basic of web development, client-server architecture (HTTP, HTTPS)
* Setting up an ASP.NET Core project
* Building endpoints and handling requests
* Returning data from APIs
* Handling errors and status codes
* Versioning and documentation
* Working with Postman
* Content negotition and serialization

### Module 10: Advanced ASP.NET Core Concepts

* Middlewares
* Dependency injection
* Introduction to authentication and authorization
* Implement token based authentication using JWT
* Role-based authorization and policies
* REST API development and resource naming
* REST vs GraphQL vs gRPC vs SOAP
* Logging
* Introduction to caching
* In-memory caching
* Distributed caching

### Module 11: Software Design Principles

* Introduction to design principles
* SOLID: Single Responsibility Principle
* SOLID: Open Closed Principle
* SOLID: Liskov Subsitition Principle
* SOLID: Interface Segregation Principle
* SOLID: Dependency Inversion Principle
* DRY, KISS, YAGNI principles

### Module 12: Software architecture and non-GoF Design Patterns

* Introduction to Software architecture
* N-Tier Architecture
* Unit of Work and Generic Repository Patterns
* Implementing N-tier architecture

### Module 13: Testing and debugging

* Introduction to Unit Testing
* Testing basics and testing frameworks
* Anatomy of a Unit Test
* Unit Testing REST APIs
* Testing Data Access Layer
* Parameterized tests and test data
* Test doubles and Mocking
* Test suites and test organization
* Test coverage and code analysis
* Advanced testing techniques

### Module 14: Deployment and Continuous Integration

* Publishing ASP.NET Core applications
* Introduction to Deployment and CI/CD
* Setting up windows server for deployment
* Introduction to github actions
* Building and testing with github actions
* Deploying to windows server with github actions
* Handling environment-specific configurations
* Automanted versioning and release management
* Deployment strategies and rollbacks
* Docker and containerization in deployment
* Monitoring and alerts
* Integration testing and quality checks

### Module 15: Advanced technologies and architecture in .NET

* Introduction to advanced .NET technologies
* RabbitMQ and Messaging
  1. Introduction to messaging and RabbitMQ
  2. RabbitMQ architecture and components
  3. Publish-subscribe model with RabbitMQ
  4. Direct messaging and Rrouting
  5. Topics and routing patterns
  6. Request-reply communication
  7. Message Acknowledgment and delivery guarantees
  8. Dead letter exchanges and message handling
  9. Message Serialization and best practices
  10. Managing RabbitMQ instances
  11. Monitoring and troubleshooting
  12. Real-world use cases and examples
* Microservices Architecture
  1. Introduction to Microservices architecture
  2. Design principles for microservices
  3. Decomposing monolitcs into microservices
  4. Service communication and API gateways
  5. Service discovery and load balancing
  6. Data management in microservices
  7. Event-Driven microservices
  8. Microservices security and authentication
  9. Testing and deployment strategies
  10. Monitoring and observability
  11. Scaling microservices
  12. Real-world use cases and case studies
* Clean Architecture
  1. Introduction to Clean Architecture
  2. Implementing the presentation layer
  3. Application services and use cases
  4. The Domain Layer and Domain entities
  5. Repository pattern and data persistence
  6. Dependency injection and infrastructure
  7. Decoupling with interfaces and Adapters
  8. Handling cross-cutting concerns
  9. Testing in Clean Architecture
  10. Achieving separation of concerns
  11. Real-world applications and case studies
* Docker and Containerization
  1. Introduction to Docker and Containers
  2. Docker fundamentals and concepts
  3. Containerizing ASP.NET Core applications
  4. Managing application dependencies
  5. Configuration and environment variables
  6. Networking and communication
  7. Persistent Storage and data volumes
  8. Docker compose for multi-container applications
  9. Orchestration with Kubernetes
  10. Docker and CI/CD
  11. Security and best practices
  12. Debugging and troubleshooting
  13. Real-world use cases and case studies
* Event Sourcing and CQRS
  1. Introduction to Event Sourcing and CQRS
  2. Event Sourcing fundamentals
  3. Implementing Event Sourcing in ASP.NET Core
  4. CQRS overview
  5. Implementing CQRS in ASP.NET Core
  6. Building the write side of CQRS
  7. Building the read side of CQRS
  8. Event store and data storage
  9. Scaling and eventual consistency
  10. Applying Event Sourcing and CQRS in real-world scenarios
  11. Pitfalls, challenges and best practices
  12. Event sourcing and CQRS with Advanced technologies
* GraphQL and API Design
  1. Introduction to GraphQL and Hot Chocolate
  2. Defining GraphQL Schemas and Types
  3. Building queries and resolvers
  4. Mutations and Data modification
  5. Fragments and reusability
  6. Filtering and pagination
  7. Authentication and authorization
  8. Real-time communitcation with subscriptions
  9. Error handling and resilience
  10. Introspection and scheme stitching
* Real-time communication with SignalR
  1. Introduction to real-time communication and SignalR
  2. SingalR fundamentals and concepts
  3. Building real-time applications with SignalR
  4. SignalR hubs and communications
  5. Real-time data visualization with SignalR
  6. Handling connection state and reconnection
  7. Scaling SignalR applications
  8. Authentication and authorization with SignalR
  9. Handling offline clients and state persistence
  10. Extending SignalR for advanced scenarios
  11. Real-world use cases and case studies
  12. Pitfalls, challenges and best practices
  13. Integrating SignalR with other technologies

### Module: 16: Design Patterns

* Introduction to Design Patterns
* Creational Patterns
  1. Singleton Pattern
  2. Factory Method Pattern
  3. Abstract Factory Pattern
  4. Builder Pattern
  5. Prototype Pattern
* Structural Patterns
  1. Adapter Pattern
  2. Bridge Pattern
  3. Composite Pattern
  4. Decorator Pattern
  5. Facade Pattern
  6. Flyweight Pattern
  7. Proxy Pattern
* Behavioral Patterns
  1. Chain of Responsibility Pattern
  2. Command Pattern
  3. Interpreter Pattern
  4. Iterator Pattern
  5. Mediator Pattern
  6. Memento Pattern
  7. Observer Pattern
  8. State Pattern
  9. Template Method Pattern
  10. Visitor Pattern

### Module 17: Desktop development in WPF

* Introduction to WPF
  1. Overview of Windows Presentation Foundation.
  2. XAML (eXtensible Application Markup Language) basics.
  3. Key differences between WPF and Windows Forms.
* XAML and UI layout
  1. Understanding XAML syntax and structure.
  2. Creating UI layouts with panels (StackPanel, Grid, DockPanel).
  3. Styling and theming using XAML.
* Data binding in WPF
  1. Implementing data binding using XAML.
  2. Two-way data binding and updates.
  3. Data templates for visualizing data.
* WPF controls and user interface
  1. Exploring built-in controls (TextBox, Button, ListBox, etc.).
  2. Customizing control appearance using styles and templates.
  3. Creating responsive and adaptive user interfaces.
* Command binding and MVVM pattern
  1. Implementing command binding for user interactions.
  2. Introduction to the MVVM (Model-View-ViewModel) architectural pattern.
  3. Separation of concerns with data binding and view-models.
* Animations and visual effects
  1. Adding animations to elements (transitions, storyboards).
  2. Using Visual States for complex UI behaviors.
  3. Enhancing user experience with visual effects.
* Navigation and page management
  1. Navigating between different views or pages.
  2. Passing data between views during navigation.
  3. Implementing a navigation framework.
* Advanced styling and control templates
  1. Creating custom control templates.
  2. Styling controls using triggers and setters.
  3. Incorporating vector graphics and icons.
* Data validation and error handling
  1. Implementing data validation using validation rules.
  2. Displaying validation errors to users.
  3. Handling exceptions gracefully.
* Localization and globalization
  1. Designing applications for internationalization.
  2. Localizing user interface elements.
  3. Handling different cultures and languages.
* Printing and reporting
  1. Generating and printing reports in WPF.
  2. Configuring print settings and page layout.
  3. Exporting content to various formats.
* Advanced topics in WPF
  1. Working with 3D graphics and animations.
  2. Integrating multimedia (audio, video) into applications.
  3. Data visualization using charts and graphs.
* Deployment and distribution
  1. Packaging WPF applications for deployment.
  2. Creating installer packages.
  3. Ensuring updates and maintenance.

### Module 18: Mobile development in .NET MAUI

* Introduction to .NET MAUI
  1. Introduction to .NET MAUI and cross-platform development.
  2. Advantages and use cases of .NET MAUI.
* Setting up the development environment
  1. Installing .NET MAUI workload and tools.
  2. Creating a new .NET MAUI project.
* Introduction XAML for .NET MAUI
  1. XAML basics: UI elements, attributes, namespaces.
  2. Building user interfaces using XAML.
* UI components and controls
  1. Using common controls: Button, Label, Entry, etc.
  2. Layouts and containers: StackLayout, Grid, FlexLayout.
* Component-based development
  1. Adding and styling toggle buttons.
  2. Implementing checkboxes and radio buttons.
  3. Creating and customizing switches.
* Data binding in .NET MAUI
  1. Data binding basics using XAML.
  2. Binding to properties in view models.
  3. Handling data updates and synchronization.
* Navigation and routing
  1. Implementing navigation between pages/views.
  2. Passing parameters between pages.
  3. Handling navigation events and patterns.
* Platform-specific customization
  1. Leveraging platform-specific APIs and features.
  2. Using Dependency Injection for platform-specific code.
* Styling and theming
  1. Applying styles using XAML resources.
  2. Theming for consistent UI across platforms.
* Handling device features
  1. Accessing device capabilities through APIs.
  2. Using Essentials library for common device features.
* MVVM pattern with .NET MAUI
  1. Understanding MVVM architecture.
  2. Binding view models to views.
  3. Commands and view model interactions.
* Localization and globalization
  1. Designing apps for multiple languages.
  2. Localizing user interface elements.
  3. Handling date, time, and number formats.
* Working with media and multimedia
  1. Displaying images and icons.
  2. Integrating audio and video content.
* Advanced .NET MAUI concepts
  1. Adaptive UI for different screen sizes and orientations.
  2. Custom controls and renderers.
  3. Integrating third-party libraries using NuGet.
* Debugging and testing
  1. Debugging .NET MAUI applications.
  2. Writing unit tests for view models and logic.
* Deployment and distribution
  1. Preparing apps for deployment.
  2. Deploying to app stores: iOS, Android, Windows.

### Module 19: Frontend development in Blazor

* Introduction to Blazor
  1. What is Blazor and its core concepts.
  2. Advantages of using Blazor for frontend development.
  3. Comparison between server-side Blazor and WebAssembly Blazor.
* Setting up the development environment
  1. Installing .NET SDK and Blazor tools.
  2. Creating a new Blazor project.
* Blazor components and pages
  1. Understanding Blazor components and Razor syntax.
  2. Creating and structuring Blazor pages.
  3. Layouts, partial views, and reusable components.
* Data binding and events
  1. Two-way data binding using `@bind` directive.
  2. Handling user interactions with events.
  3. Using form controls and input validation.
* Routing and navigation
  1. Configuring routing in Blazor applications.
  2. Navigating between different pages and views.
  3. Passing parameters in routes.
* State management
  1. Managing component state with `@state`.
  2. Sharing state between components.
  3. Using Cascading Parameters.
* Forms and validation
  1. Building forms with Blazor components.
  2. Client-side and server-side form validation.
  3. Displaying validation errors to users.
* Layouts and UI styling
  1. Creating consistent layouts using shared components
  2. Styling components with CSS and Bootstrap.
  3. Customizing UI using themes and templates.
* Dependency injection in Blazor
  1. Understanding DI in Blazor applications.
  2. Registering services and injecting dependencies.
  3. Implementing services for data access.
* Working with APIs and HTTP requests
  1. Making HTTP requests using HttpClient.
  2. Consuming RESTful APIs and handling responses.
  3. Authentication and authorization with APIs.
* Client-side interactivity
  1. Adding JavaScript interop for client-side functionality.
  2. Incorporating third-party JavaScript libraries.
* Component lifecycle and hooks
  1. Understanding the lifecycle of a Blazor component.
  2. Using lifecycle methods (`OnInitialized`, `OnParametersSet`, etc.).
  3. Performing actions during component lifecycle.
* WebAssembly Blazor (Experimental)
  1. Introduction to WebAssembly Blazor.
  2. Setting up and building WebAssembly applications.
  3. Comparing WebAssembly and server-side Blazor.
* Testing and debugging
  1. Writing unit tests for Blazor components and logic.
  2. Debugging Blazor applications in the browser.
* Deployment and hosting
  1. Publishing Blazor applications for deployment.
  2. Hosting options (Azure, AWS, GitHub Pages, etc.).
* Advanced topics and best practices
  1. Advanced state management with Flux/Redux patterns.
  2. Using Blazor with Progressive Web Apps (PWAs).
  3. Real-time communication with SignalR and Blazor.
  4. Performance optimization and lazy loading.
  5. Integrating Blazor with authentication providers.

### Module 20: Building a real-world projects

* Delivering system (BARQ, Talabat)
* Producing real-world package for Nuget
* Contribution in real-world exist open-source projects



