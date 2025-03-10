# Port security

## Overview

In this section, you will learn how to use `.env` files and variables to protect and prevent the port value from cyber attacks.

## Issue:

When deploying to different environment and teams, it's essential for maintaining security and flexibility or else everybody include strangers(e.g hackers and intruders) can access the server through the leaked port.

Bad example of port security:

```title="bad-example.ts" linenums="1"
const app = express();

const PORT: number = 3000;

app.set("view engine", "ejs");

app.get("/", (req, res) => {
  res.render("index.ejs");
});
```

## How to access environment variables for port

The `.env` file can store your application's sensitive datas such as the port number in environment variables.

Example of `.env` file:

```env title="example.env"

PORT=3000


```

## Using `dotenv` in JavaScript:

In JavaScript, you'll use `require()` to load and parses the dotenv module, and then access environment variables by using `process.env`

Example of JavaScript:

```js title="dotenv.js" linenums="1"
require("dotenv").config();

const port = process.env.PORT || 5000;

console.log(`Server is running on port: ${port}`);
```

Explainations:

- `require('dotenv').config()` loads and parses the .env file.
- `process.env.PORT` retrieves the value of the PORT variable. If PORT is not defined in the .env file, it will default to `5000`

## Using `dotenv` in TypeScript:

In TypeScript, you will need to import the dotenv module using `import` and also define the types as `string` for `process.env` to not get error when type-checking.

Example of TypeScript:

```ts title="dotenv.ts" linenums="1"
import dotenv from "dotenv";
dotenv.config();

const port: string = process.env.PORT || "5000";

console.log(`Server is running on port: ${port}`);
```

Explainations:

- `import dotenv from "dotenv";`, and `dotenv.config();` allows you to import and configure the dotenv library in TypeScript.
- The environment variable `process.env.PORT` will be a string, so you can assign it directly to a string variable.

In addition, In TypeScript, you can enhance type safety by creating a custom interface for process.env. This ensures that TypeScript knows about the specific environment variables you are using.

Example of Adding Type Safety:

```ts title="type-safety.ts" linenums="1"
import dotenv from "dotenv";
dotenv.config();

interface ProcessEnv {
  PORT: string;
}

const port: string = (process.env as ProcessEnv).PORT || "5000";

console.log(`Server is running on port: ${port}`);
```

Explainations:

- The `ProcessEnv` interface defines the specific environment variables that will be used in the application.
- By casting `process.env` to `ProcessEnv`, TypeScript will know about the PORT variable, ensuring type safety.

## Conclusion

- By using the `dotenv` library, you can securely manage sensitive data like port values without hardcoding them into your application code. This practice is essential for maintaining security and flexibility, especially when deploying to different environments or teams.

- Whether you are working in JavaScript or TypeScript, dotenv provides a simple and efficient way to keep environment variables in a .env file, which can be easily loaded and used in your application.
