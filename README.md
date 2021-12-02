<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## @Module Decorator Properties

- `providers`: array of providers to be available within the module via dependency injection.

- `controllers`: array of controllers to be instantiated within the module.

- `exports`: array of providers to export to other modules.

- `imports`: list of modules required by this module. Any exported `provider` by these modules will now be available in our module via dependency injection.

## NestJS Providers

- Can be injected into constructors if decorated as an `@Injectable`, via dependency injection.

- Can be a plain value, a class, sync/async factory...

- Providers must be provided to a module for them to be usable.

- Can be exported from a module - and then be available to other modules that import it.

## Service

- Defined as providers. Not all providers are services.
- Singleton when wrapped with `@Injectable()` and provided to a module.
- The main source of business logic. Ex: a service will be called from a controller to validate data, create an item in the database and return a response.

- `@Injectable()` is used to define that a certain class should have a shared instance across the module. The instance can then be injected using Dependency Injection, and all injectors will have access to the same instance and its state.

## Other terms

- A DTO is <b>NOT</b> a model definition. It defines the shape of data for a specific case.
- Interfaces are a part of Typescript and therefore are not preserved post-compilation.
- NestJS cannot refer to interfaces in run-time, but can refer to classes.

## Installation

```bash
$ npm install
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```
