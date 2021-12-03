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

## Pipes
### Definition
- Pipes operate on the **arguments** to be processed by the route handler, just before the handler is called.
- Pipes can perform **data transformation** or **data validation**.
- Pipes can return data - either original or modified - which will be passed on to the route handler.
- Pipes can throw exceptions. Eceptions thrown will be handled by NestJS and parsed into an error response.
- Pipes can be asynchronous.
### Custom Pipe Implementation
- Pipes are classes annotated with the `@Injectable()` decorator.
- Pipes must implement the `PipeTransform` generic interface. Therefore, every pipe must have a `transfrom()` method. This method will be called by NestJS to process the arguments.
- Whatever is returned from the `transform()` method will be passed on to the route handler. Exceptions will be sent back to the client.
- **Handler-level pipes** are defined at the handler level, via the **@UsePipes()** decorator. Such pipe will process all parameters fo the incoming requests.
```js
@Post()
@UsePipes(SomePipe)
createTask(@Body('description') desciption) {...}
```
- **Global pipes** are defined at the application level and will be applied to any incoming request.
```js
async function bootstrap() {
  const app = await NestFactory.create(ApplicationModule);
  app.useGlobalPipes(SomePipe);
  await app.listen(3000);
}
```
## Other terms

- A DTO is **NOT** a model definition. It defines the shape of data for a specific case.
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
