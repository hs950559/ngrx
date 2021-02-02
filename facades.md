# Facades in NgRx

A facade is basically just an Angular service that handles any interaction with the store. When a component needs to dispatch an action or get the result of a selector, it would instead call the appropriate methods on the facade service.

![Facades in Angular](https://cdn.auth0.com/blog/ngrx-facades/ngrx-facade-diagram.png)