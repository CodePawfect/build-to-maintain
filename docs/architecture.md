# Architecture without ceremony

Architecture should make the next change easier to understand and safer to make. Start by reading the repository's instructions, manifests, lockfiles, runtime-version files, build and CI commands, entry points, tests, and existing imports. Identify the framework and dependency versions from those signals, then use the official documentation for the versions in use. A manifest describes declared dependencies and runtime compatibility; a lockfile records the resolved tree. For example, npm documents these roles for [`package.json`](https://docs.npmjs.com/cli/v11/configuring-npm/package-json/) and [`package-lock.json`](https://docs.npmjs.com/cli/v11/configuring-npm/package-lock-json/). If a new repository has no such signals, make the stack and version an explicit product decision before scaffolding it.

## Choose structure that fits the language

A directory groups files. A language package may define imports, visibility, or an API. A module may define a dependency, build, or release unit. A workspace commonly coordinates several units. These words mean different things across ecosystems, so preserve the repository's existing build model and follow the language and framework's conventions. In Go, for example, one `go.mod` module can contain multiple packages in separate directories; the official layout guide shows different arrangements for libraries, commands, and servers. Its `internal` directory also restricts who can import implementation packages. These are Go conventions, not a universal folder recipe. See [Organizing a Go module](https://go.dev/doc/modules/layout) and [Effective Go](https://go.dev/doc/effective_go).

For application code, start with a feature-first directory when several features exist: keep the files that change together near each other and expose only the small surface other features need. A directory does not automatically need to become a separately versioned package, build target, or service. Split those units only when independent dependencies, releases, ownership, or deployment provide a real benefit. Use names and shapes already familiar in the stack.

```text
src/
  orders/
    create-order.ts
    order.ts
    order-store.ts
    http.ts
  catalog/
    search.ts
    product.ts
```

This is an illustrative feature grouping. A small project may need only one cohesive feature directory or a few files in the framework's standard layout.

## Keep the design small and responsibilities cohesive

Build one useful path end to end before adding scaffolding for hypothetical features. Prefer the fewest concepts that keep current behavior clear. In this playbook, an abstraction earns its place by protecting a boundary, supporting meaningful implementations, reducing duplicated policy, or isolating a useful test seam. Avoid empty layers and one-interface-per-class wrappers that only rename a call.

Single Responsibility means one coherent reason to change, not one method per class. Ask whether a module groups rules that change for the same business reason or owner. If pricing policy and HTTP parsing repeatedly change for unrelated requests, give them separate homes. If they always change together, splitting them may only scatter the work. Robert C. Martin explains SRP in terms of reasons a module changes and the people or functions that request the change: [The Single Responsibility Principle](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html).

Extract a function when a cohesive block takes effort to interpret and a name can reveal its purpose at the call site. Name it for what it decides or accomplishes, not for the mechanics hidden inside. This lets readers follow the main path without reopening every detail, as Fowler describes in [Function Length](https://martinfowler.com/bliki/FunctionLength.html) and demonstrates in [Extract Function](https://refactoring.com/catalog/extractFunction.html). There is no useful universal line-count threshold: keep an obvious expression inline, and reconsider an extraction whose name is vague or whose behavior is harder to understand than the original block.

## Give complex backends inward dependencies

For a larger backend with substantial business rules or several external integrations, this playbook prefers a modest hexagonal design. Keep domain rules independent of web, database, and vendor SDK types. Put an interface (port) in the inner layer that needs an external capability; put its technology-specific implementation in an adapter. Source dependencies point inward: adapters import application ports and domain types; application use cases import domain rules; domain code imports neither application nor infrastructure. A composition root at the outside imports the concrete adapters and use cases to wire them together. Runtime calls may travel back outward through a port. This is the boundary idea in [Cockburn's original Ports and Adapters description](https://alistair.cockburn.us/hexagonal-architecture).

```text
src/
  orders/
    domain/          # Order, pricing rules; no framework or database imports
    application/     # PlaceOrder use case and OrderStore port
    adapters/        # HTTP controller and Postgres OrderStore implementation
  app/
    wiring/          # creates adapters and supplies them to use cases
    main.ts

imports: adapters → application → domain
         wiring → adapters + application
```

Here the persistence adapter implements the application port; the domain does not depend on that adapter. Leave repository interfaces out of the domain unless domain behavior itself needs that concept. Keep transactions and side effects explicit at the application boundary.

This is a preference for backend complexity, not a mini-CRUD template. A simple data-entry service can stay as a cohesive framework module with direct persistence. The [Microsoft DDD microservice guide](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice) similarly distinguishes complex domain models from simple CRUD services and says the domain model should not directly depend on infrastructure frameworks. Add ports, adapters, and modules when they protect a real rule or change boundary; do not create six empty folders to satisfy a diagram.
