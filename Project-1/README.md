# Project 1: Java API
This first project will be in progress for the first three weeks of training. This will coincide with the training topics of Java, SQL, JDBC, and REST with Javalin. We will be building a server API with no front end UI, and simple authentication/authorization.

We will follow a [Multitier Architecture](https://en.wikipedia.org/wiki/Multitier_architecture) with 3 layers:
 - Presentation Layer (Web Controllers)
 - Service Layer (Business Logic)
 - Data Layer (Database Access)

## Presentation Layer
This layer should include classes which handle web communication. These classes should really only be dealing with the requests and responses. All other work should be invoked in the service layer.

We will build controllers here to handle web requests using the Javalin API library.

## Service Layer
This layer handles most of the business logic, everything that doesn't belong in the presentation or data layers. The presentation layer above invokes business operations here in the service layer. This layer then breaks those operations into individual data operations and invokes them in the data layer below.

## Data Layer
The service layer invokes operations here in the data layer in order to persist or retrieve data from some data source. Often a business operation makes multiple calls down into this layer.

We will build DAOs here to access a SQL database using the built in Java JDBC library.

