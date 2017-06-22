### Basics

*   A key powerful feature of LoopBack is that when you define a model it automatically comes with a predefined REST API with a full set of create, read, update, and delete operations. 
*   The Model definition JSON file includes an idInjection property that indicates whether LoopBack automatically adds a unique id property to a model. For a model connected to a database, the id property corresponds to the primary key.
*   Base Models > Connected Models > Built-in models
*   To specify a project-relative path (for example, to a directory containing static assets), start the string with the prefix $!

### Middleware

*   Middleware registered via the Express API app.use, app.route, app.get (and other HTTP verbs) runs at the beginning of "route" phase.
*   By convention, place middleware functions in the server/middleware directory.
*   `#` in the middleware ID is just an easy way to determine the method name e.g. loopback#static = loopback.static()
*   Middlewares can have name, method they are applied to e.g. get/post etc. Paths these should get trigger. For more info read [configuration.](http://loopback.io/doc/en/lb3/Defining-middleware.html#middleware-configuration-properties "Middleware Configuration Properties")
*   If you don’t provide the route, then the middleware will trigger on all routes

