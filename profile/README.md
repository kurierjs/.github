# Kurier

A TypeScript framework to create APIs following the [1.1 Spec of JSONAPI](https://jsonapi.org/format/1.1/) + the [Operations proposal spec](https://github.com/json-api/json-api/blob/999e6df77b28549d6c37b163b73c8e9102400020/_format/1.1/index.md#operations).

## Features

- **Operation-driven API:** JSONAPI is transport-layer independent, so it can be used for HTTP, WebSockets or any transport protocol of your choice.
- **Declarative style for resource definition:** Every queryable object in JSONAPI is a resource, a representation of data that may come from any source, be it a database, an external API, etc. Kurier defines these resources in a declarative style.
- **CRUD database operations:** Baked into Kurier, there is an operation processor which takes care of basic CRUD actions by using [Knex](https://knexjs.org/). This allows the framework to support any database engine compatible with Knex. Also includes support for filtering fields by using common SQL operators, sorting and pagination.
- **Transport layer integrations:** The framework supports JSONAPI operations via WebSockets, and it includes middlewares for [Koa](https://koajs.com), [Express](http://expressjs.com/) and [Vercel](https://vercel.com) to automatically add HTTP endpoints for each declared resource and processor.
- **Relationships and sideloading:** Resources can be related with `belongsTo` / `hasMany` helpers on their declarations. Kurier provides proper, compliant serialization to connect resources and even serve them all together on a single response.
- **Error handling:** The framework includes some basic error responses to handle cases equivalent to HTTP status codes 401 (Unauthorized), 403 (Forbidden), 404 (Not Found) and 500 (Internal Server Error).
- **User/Role presence authorization:** By building on top of the decorators syntax, Kurier allows you to inject user detection on specific operations or whole processors. The framework uses JSON Web Tokens as a way of verifying if a user is valid for a given operation.
- **Extensibility:** Both resources and processors are open classes that you can extend to suit your use case. For example, do you need to serialize an existing, external API into JSONAPI format? Create a `MyExternalApiProcessor` extending from `OperationProcessor` and implement the necessary calls _et voilà!_.
