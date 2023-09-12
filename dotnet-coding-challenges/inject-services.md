# Inject services with different lifetimes

With dependency injection in ASP.NET Core, there are three different service lifetimes that can be used:
- **Singleton**: The lifetime will last for the lifetime of the application.
- **Scoped**: The lifetime is initalised when a HTTP request has been made and is disposed of when the HTTP response has been sent. It can also be defined explicitly.
- **Transient**:  The lifetime is initalised every time a service is injected.

Most services can be injected directly into other services regardless of their lifetime. However, there is scenario where a service with a particular lifetime cannot inject a service with another service lifetime.

Can you find out which service lifetimes they are?

================================================================
## Answer
A singleton service lifetime cannot inject a scoped service lifetime directly. A service with a singleton lifetime would not know which scope instance it belongs to, so an exception would be thrown.

In-order to use a service with a scoped lifetime in a singleton service lifetime class, you would have to explictly create a scope within it and then use that scope to resolve the instance.