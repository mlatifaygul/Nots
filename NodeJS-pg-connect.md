# NodeJS PG Connect

#Terminal => 
```node
    npm i knex pg
    npm i -g knex
    npx knex init
    npx knex migrate:make <add_table>
    npx knex migrate:up 'or' migrate:latest
    npx knex seed:make <add_table_rows> //add as many rows as the number of columns.
    npx knex seed:run
```

knexfile.js => 

```js
module.exports = {
        development: {
          client: "pg",
          connection: {
            database: "arin",
            user: "admin",
            password: "admin",
          },
          pool: {
            min: 2,
            max: 10,
          },
          production: {},

          migrations: {
            directory: "./data/migrations",
          },
          seeds: {
            directory: "./data/seeds",
          },
        },
      };
```

./data/migrations/<add_table> => 

```js
      exports.up = function (knex) {
      return knex.schema
        .createTable("<tableName>", (table) => {
        
        }
        
      exports.down = function (knex) {
      return knex.schema
        .dropTableIfExists("giris_bilgi") };
```

