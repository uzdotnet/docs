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
* Why .NET?
* Major components of .NET
* Installing .NET
* Hello World in 5 minutes and .NET CLI
* Installing IDE (Visual Studio, Rider)
* Introducing project/solution structure

### Module 2: C# Fundamentals

* Date types and variables
* Input data to console
* If/else operator
* Switch/case operator
* Goto operator
* Loops, break and continue
* Math functions
* Comments

### Module 3: Essentials C# programming concepts

* Functions and params
* Ref and out
* Arrays
* String arguments in Main function
* Introduction to OOP (vs functional programing)
* Major components of OOP
* Classes and objects
* Property and fields
* Constructor and Destructor
* Inheritance and this/base keywords
* Polimorphism
* Incapsulation
* Abstraction
* Enum and struct
* static, sealed, abstract classes
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
* Asynchronoues programming
* Reflection and attributes

### Module 5: Version Control

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

### Module 6: Database

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

### Module 7: ORM

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

### Module 8: Introduction to ASP.NET Core

* Basic of web development, client-server architecture (HTTP, HTTPS)
* Setting up an ASP.NET Core project
* Building endpoints and handling requests
* Returning data from APIs
* Handling errors and status codes
* Versioning and documentation
* Content negotition and serialization

### Module 9: Advanced ASP.NET Core Concepts

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

### Module 10: Software Design Principles

* Introduction to design principles
* SOLID: Single Responsibility Principle
* SOLID: Open Closed Principle
* SOLID: Liskov Subsitition Principle
* SOLID: Interface Segregation Principle
* SOLID: Dependency Inversion Principle
* DRY, KISS, YAGNI principles

### Module 11: Software architecture and non-GoF Design Patterns

* Introduction to Software architecture
* N-Tier Architecture
* Unit of Work and Generic Repository Patterns
* Implementing N-tier architecture

### Module 12: Testing and debugging

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

### Module 13: Deployment and Continuous Integration

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

### Module 14: Advanced technologies and architecture in .NET

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

### Module: 15: Design Patterns

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

### Module 16: Building a real-world projects

* Delivering system (BARQ, Talabat)
* Producing real-world package for Nuget
* Contribution in real-world exist open-source projects



