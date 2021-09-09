
# 💻 E-Commerce 🛍️ Back End

This is a back end application that uses MySQL2 and Sequelize to create tables for an e-commerce database and perform all [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) operations for each table. The user can add, view, update, and delete categories, products, and tags.

---

## Table of Contents
* [Technologies](#technologies)
* [Functionality](#functionality)
* [Challenges](#challenges)
* [Future Development](#future-development)
* [Contact](#contact)
* [License](#license)


## Technologies

![MySQL](https://img.shields.io/badge/MySQL-coral?style=for-the-badge&logo=mysql&logoColor=darkblue)&nbsp;
![Sequelize](https://img.shields.io/badge/Sequelize-blue?style=for-the-badge&logo=Sequelize)&nbsp;
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)&nbsp;
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)&nbsp;
![Insomnia](https://img.shields.io/badge/Insomnia-5849be?style=for-the-badge&logo=Insomnia&logoColor=white)&nbsp;


## Functionality

[App Demonstration  Video](https://youtu.be/K3uBsWA2X5M)


### App Initialization
* Be sure to first run <code>npm i</code> after cloning this repo or copying its code into your own files.
* This code uses a `.env` file, which is configured in `connection.js` through the [dotenv](https://www.npmjs.com/package/dotenv) package. If you clone this repo or copy its code, you will need to adjust the variables in `connection.js`, or otherwise create your own `.env` file.
* Once the appropriate node modules have been installed and you have set up your `connection.js` with or without a `.env` file, run the following:
    * `mysql -u root -p`, followed by your MySQL password
    * `source ./db/schema.sql;`
    * `exit`
    * `npm run seed`
    * `npm start`
* From there, the app will be listening on port 3001, so you can go to Insomnia


## Challenges
* Mostly, the challenges in this project were overcome by reviewing documentation, further research, and trial and error.
* Due to (what I consider to be) fairly incomplete/inconsistent/misleading documentation for Sequelize, I found it difficult at first to accomplish two specific things:
    * Include information from multiple other tables, as in `product-routes.js` at line 11. I found this solution: `include: { all: true, nested: true }` but it felt wrong somehow. Through deeper research and seeing other people with similar questions, I learned that there was a more specific way, which made it into the final code.
    * Correctly place the `onDelete: 'CASCADE'`; It was unclear from documentation how that parameter in the associations would work - specifically, which direction the cascade would occur. Does the `onDelete` refer to the source or the target? I'm still not 100% sure about this, but I think I determined that putting it on both sources in a one-to-many relationship will work. In terms of this project - deleting a Category would delete all Products within that Category, and deleting a Product would cascade to delete that product's row within the table of its Category. The way I implemented this seems to work, but I would love if someone with a better understanding could clarify, since the documentation seems unable to do so.


## Future Development
* Create a front end to accompany it, so users can perform the same tasks using a GUI.


## Contact
Email me any time with questions, comments, or cat/dog photos! - ctbarrett.tech@gmail.com


## License
&copy; 2021 Charles Tucker Barrett

[MIT License](https://opensource.org/licenses/MIT)