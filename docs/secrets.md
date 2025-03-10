# Hiding Secrets

## Overview

In this section, authentication for hiding Secrets for sessions and password hashing will be covered. This allows for users that are logged into a web-application, to be kept safe from any hackers and unauthorized users.

Hiding these keys are vital to keeping your user's information safe. It isolates key factors (variables) that are used to decrypt/uncode/reveal a user's data from your code base.

## Session Secrets

When making sessions for users using the npm library **cookie-session**, you must make sure to hide the values of the cookies, as any attacker can use that value and infilitrate the user's data.

Observe the **cookie-session** middleware below:

![](/assets/secrets_screenshot1.png)

This code is a simple snippet of the cookie-session library containing hard-coded values into the cookie-session's name and key.

!!! warning

    This is dangerous since attackers can use these values to impersonate or take over user accounts as the secrets are visible to anybody in the codebase.

### Hiding Session Secrets

1. Insert your values into the .env file by assigning them variables.

   ```title=".env" linenums="1"
   SESSION_NAME_SECRET="whoami"
   SESSION_KEY_SECRET="ILHTonTOP"
   ```

!!! note

    Remember to follow _**.env**_ variable naming conventions, you may also want to make your secrets complex by making a long secret, adding special characters, and using uppercase/lowercase letters. This increases the time it takes for brute force attacks to succeed.

2. Apply your environment variables into your session options object.

   ```title="index.ts" linenums="1"
   import cookieSession from "cookie-session"

   app.use(cookieSession({
      name: process.env.SESSION_NAME_SECRET
      keys: [process.env.SESSION_KEY_SECRET]
   }));
   ```

   Congratulations, you have secured your cookie-sessions

## Bcrypt Salt Rounds

User passwords using bcrypt on your web applications are hashed to prevent attackers from seeing passwords in plain text.

This is applied by giving your salt rounds a number value.
![](/assets/promise.png)

The vulnerable data here is the salt rounds as the number 24 can be used to evaluate the strength of your hashing process, significantly reducing the time it takes for a hacker to take over your data.

## Hiding your salt rounds

The following steps will walk you through securing your salt rounds.

1.  In your _**.env**_ file, add a variable named **BCRYPT_SALT_ROUNDS**

    ```title=".env" linenums="1"
    BCRYPT_SALT_ROUNDS=<insert the # of salt rounds here>
    ```

2.  Just like accessing your **cookie-session** environment variables, replace your salt round values with **process.env.BCRYPT_SALT_ROUNDS**
    ```title="index.ts" linenums="1"
    const hashRegisteredPassword = async (password: string): Promise<string> => {
    	const hashedPassword: Promise<string> = await bcrypt.hash(password, process.env.BCRYPT_SALT_ROUNDS);
    	return hashedPassword;
    }
    ```
    ```title="index.js" linenums="1"
    	const hashRegisteredPassword = async (password) => {
    		const hashedPassword = await bcrypt.hash(password, process.env.BCRYPT_SALT_ROUNDS);
    		return hashedPassword;
    	}
    ```
    You have now secured your user's passwords!

### Conclusion

By the end of this section, you have learned:

- Vulnerabilities in your session and bcrypt libraries.
- The outcome of unconcealed authentication data.
- How to hide your authentication data.
