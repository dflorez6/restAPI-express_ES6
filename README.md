# README | API REST with Node & Express (ES6)

## Express (Web Server)
* To install express, from the console:
    > npm install express

* To make it work with ES6 import/export modules, go to package.json and add the following:

        "type": "module"

* Also add the following inside scripts { }:

        "start": "node --experimental-specifier-resolution=node index",

## ENV Variables (dotenv)
https://www.youtube.com/watch?v=PxshhOKNPpQ
* From the terminal run:
    
    > npm install dotenv

* Inside index.js (server config file) add the following:
    
        //====================
        // ENV
        //====================
        // Fix for __dirname && __filename in ES6
        import path from 'path';
        import { fileURLToPath } from 'url';
        const __filename = fileURLToPath(import.meta.url);
        const __dirname = path.dirname(__filename);

        // Import dotenv
        import dotenv from 'dotenv';
        dotenv.config({ path: path.resolve(__dirname, './.env') })

* To use ENV variables in the code:

        process.env.ENV_NAME
        // Example PORT=3000 will be the ENV variable used
        process.env.PORT

## Library: Unique Identifier - uuid
* In case the app doesn't use a db and we want to generate unique identifiers, from the terminal:
    
    > npm install uuid

* Inside index.js (server config file) add the following:

        import { v4 as uuidv4 } from 'uuid';

## Library: Cross-Origin Resource Sharing - CORS
* Install from the terminal:
    
    > npm install cors

* Inside index.js (server config file) add the following:

        const cors = require('cors');
        app.use(cors()); // To enable CORS requests on all routes

* In case you want to use CORS on specific routes, inside index.js:

        var cors = require('cors')
        // Then on the route
        app.get('/products/:id', cors(), function (req, res) {
            res.json({msg: 'This is CORS-enabled for a Single Route'})
        })
        
## API Calls from terminal using cURL
* To test API endpoints with cURL from the terminal:

    > curl http://localhost:3000
    > -> Received a GET HTTP method

    > curl -X POST http://localhost:3000
    > -> Received a POST HTTP method

    > curl -X PUT http://localhost:3000
    > -> Received a PUT HTTP method

    > curl -X DELETE http://localhost:3000
    > -> Received a DELETE HTTP method

## Dependencies
* express-session
* express-validator
* mongoose