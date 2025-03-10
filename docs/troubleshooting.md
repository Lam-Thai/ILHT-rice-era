# Troubleshooting

## Overview

This section will show you how to debug and resolve any problems/issues that you meet when you implement the codes.

## Step by step guide

### Check format and syntax of the `.env` file

Ensure your `.env` file format correctly. It should not be any spaces before/after the keys or values.

Example of correct format:

```env title="good-format.env" linenums="1"
API_KEY=your-api-key
DB_HOST=localhost
DB_PORT=5432
```

Common mistakes:

- Spaces before or after the `=`sign.
- Missing `=` for key-value pairs.
- Non-ASCII characters or special characters that might cause issues.

### Verify if the `dotenv` module required correctly

Ensure that you need to require `dotenv` module at the very top of your javascript before you implement any other code.

Example of Javascript:

```js title="example.js" linenums="1"
const process = require("dotenv").config();

const port = process.env.PORT || 5000;
```

Output if you have the name in `js` and `.env` don't match:

![](/assets/portwrong.png)

In addition, your values in `javascript` file should be matched with ones in the `.env` file. For instance, if your .env file has `API_KEY=your-api-key`, ensure that your code accesses it as `process.env.API_KEY`, not something like `process.env.VALUE`

### Logging the error in console

Try `console.log()` the values to see if they are loaded and parsed to the javascript file correctly.

```js title="console.js" linenums="1"
console.log(process.env.PORT);
```

Explanations:

- If the output give you `undefined`, this means you not parse the values correctly. Check the `.env` file or all the syntax/formats in your javascript file.

### Validate environment variables by error handler

Validate that the environment variables are defined properly. For instance, before trying to use a variable, you can check if it's defined

Example of Javascript:

```js title="validate.js"
if (!process.env.PORT) {
  console.error("PORT is not defined in .env file");
}
```

Output of your console:

![](/assets/console_error.png)

### Use `dotenv` debug mode

If you want to know how your `dotenv` module work. You can enable the debug mode by putting `debug: true` in `config()`

Example of JavaScript:

```js title="debug.js"
require("dotenv").config({ debug: true });
```

Output of your console if you turn on the debug mode:

![](/assets/debug_mode.png)

Explaination:

- This will log to the console information about the .env file being loaded and any errors encountered.

### Check compatibility with other libraries

Some libraries or frameworks (e.g., webpack or Next.js) might have specific methods or considerations for loading environment variables, which may interfere with dotenv. Ensure you are following any framework-specific guidelines.

## Common Issues

1. Error: Cannot find module 'dotenv':

   - Solution: Run `npm install dotenv` to ensure the library is installed.

2. process.env.VARIABLE_NAME is undefined:

   - Solution: Double-check that the key exists in the `.env` file and that it is being parsed correctly in your `javascript` file.

3. Error: ENOENT: no such file or directory, open `.env`:

   - Solution: Ensure that your `.env` file exists in the correct directory, and verify that dotenv.config() is pointing to the correct path for the `.env` file.

4. Environment variable is not being loaded properly:

   - Solution: Try logging the `process.env` object to verify the loaded environment variables, or use dotenv.config({ debug: true }) to gather more details about what might be failing.

## Addition resources

- [Dotenv Documentation](https://www.npmjs.com/package/dotenv)
