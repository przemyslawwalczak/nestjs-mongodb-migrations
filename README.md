# NestJS MongoDB Migrations

A work in progress.

## About

TODO:
1. Creates and runs migrations for MongoDB.
2. Typescript out-of-the-box.
3. Recommended migration state storage in collection.
4. Provides post-generator api for producing generated types/enums/or any extra files after migrations has been ran.

## Installation

```
yarn add @przemyslawwalczak/nestjs-mongodb-migrations
```

## Configuring

Simple and extensive configuration.

### With NestJS

```ts
    import { MongodbMigrationsModule } from '@przemyslawwalczak/nestjs-mongodb-migrations';

    MongodbMigrationsModule.forRoot({
        connect: '<mongodb-connection-uri>',
        database: 'example',
        
        migrations: {
            directory: './migrations',
            runOnModuleInit: false,
            collection: 'migration', // migration collection by default
            generators: []
        }
    })

    import { MongodbMigrations } from '@przemyslawwalczak/nestjs-mongodb-migrations'

    async function setup() {
        const app = '<create-nestjs-app>'

        await app.get(MongodbMigrations.getServiceToken()).runMigrations()
    }
```