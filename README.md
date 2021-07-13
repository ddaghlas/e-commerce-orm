# E-Commerce Back-End Utilizing Object-Relational Mapping

## Description
- Internet retail, also known as **e-commerce**, is the largest sector of the electronics industry requiring full-stack web development. 
- My task was to build the back end for an e-commerce site by modifying starter code. It required configuration of a working Express.js API to use Sequelize to interact with a MySQL database. The company's requirements were to include a back end that uses the latest technologies, allowing them to compete with other e-commerce companies. 
- The application is not deployed but example tutorials for installation and functionality can be found below. I have included a step by step installation guide as well, if the applcation would like to be forked. 


  ## Table of Contents
  * [Installation](#installation)
  * [Usage](#usage)
  * [Contributing](#contributing)
  * [Tests](#tests)
  * [License](#license)


## Installation

```md
- GIVEN a functional Express.js API
- WHEN adding database name, MySQL username, and MySQL password to an environment variable file
- THEN the ability to connect to a database using Sequelize is created
- WHEN schema and seed commands are entered
- THEN a development database is created and is seeded with test data
- WHEN the command to invoke the application is entered
- THEN the server is started and the Sequelize models are synced to the MySQL database
- WHEN API GET routes is opened in Insomnia Core for categories, products, or tags
- THEN the data for each of these routes is displayed in a formatted JSON
- WHEN API POST, PUT, and DELETE routes are tested in Insomnia Core
- THEN data is successfully created, updated, and deleted within the database
```

## Usage

- Installation requires the use of the [MySQL2](https://www.npmjs.com/package/mysql2) and [Sequelize](https://www.npmjs.com/package/sequelize) packages to connect the Express.js API to a MySQL database and the [dotenv](https://www.npmjs.com/package/dotenv) package to use environment variables to store sensitive data.

- Use the `schema.sql` file in the `db` folder to create a private database with MySQL shell commands. Use environment variables to store sensitive data like the MySQL username, password, and database name.



The following animation shows the application's GET routes to return all categories, all products, and all tags being tested in Insomnia Core:

![In Insomnia Core, the user tests “GET tags,” “GET Categories,” and “GET All Products.”.](./images/GET-cpt.gif)

The following animation shows the application's GET routes to return a single category, a single product, and a single tag being tested in Insomnia Core:

![In Insomnia Core, the user tests “GET tag by id,” “GET Category by ID,” and “GET One Product.”](./images/GET-single.gif)

The following animation shows the application's POST, PUT, and DELETE routes for categories being tested in Insomnia Core:

![In Insomnia Core, the user tests “DELETE Category by ID,” “CREATE Category,” and “UPDATE Category.”](./images/POST-category-orm.gif)

The following animation shows the application's POST, PUT, and DELETE routes for products being tested in Insomnia Core:

![In Insomnia Core, the user tests “DELETE Products by ID,” “CREATE Product,” and “UPDATE Product.”](./images/POST-prod.gif)

The following animation shows the application's POST, PUT, and DELETE routes for tags being tested in Insomnia Core:

![In Insomnia Core, the user tests “DELETE Tags by ID,” “CREATE Tags,” and “UPDATE Tags.”](./images/POST-tags.gif)


### Associations

To execute association methods on the Sequelize models the following relationships were created between them:

* `Product` belongs to `Category`, and `Category` has many `Product` models, as a category can have multiple products but a product can only belong to one category.

* `Product` belongs to many `Tag` models, and `Tag` belongs to many `Product` models. Allow products to have multiple tags and tags to have many products by using the `ProductTag` through model.

* Foreign key relationships were created that match the column created in the respective models.

### API Routes refactored to Perform RESTful CRUD Operations

* Refactored the unfinished routes in `product-routes.js`, `tag-routes.js`, and `category-routes.js` to perform create, read, update, and delete operations using the Sequelize models created. The functionality for creating the many-to-many relationship for products had already been completed. 

* Syntax was key for this ORM project to be able to use the model's column definitions to `req.body` for POST and PUT routes.

## Tests
### Seed the Database

After creating the models and routes, `npm run seed` is run in the terminal to seed data to the database to be able to test the routes.

### Sync Sequelize to the Database on Server Start

Create code for `server.js` to sync the Sequelize models to the MySQL database on server start.

