# Hiding Secrets

## Overview

In this section, hiding Secrets for sessions and password hashing will be covered. This allows for users that are logged into a web-application, to be kept safe from any hackers and unauthorized users.

Hiding these keys are vital to keeping your user's information safe. It isolates key factors (variables) that are used to decrypt/uncode/reveal a user's data from your code base.

## Session Secrets

Observe the code below:

![](/assets/secrets_screenshot1.png);

This code is a simple snippet of the session library containing hard-coded values into it's options.

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
