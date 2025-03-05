# Using .gitignore

## Overview

In this section, you will know how to use `.gitignore` to securely hide all the environment variables for sensitive information that being store in `.env` file before committed to version control (e.g Git).

## How to use

The `.gitignore` file is to recognize and tell Git what files and directories to ignore while staging and pushing, in order to ensure that your `.env` never committed, you need to add it to `.gitignore`.

### Step by step

- If you don't already have one, creating a `.gitignore` file in your project's directory.
- Open the file and adding manually into it to ignore the `.env` file:

```bash title=".gitignore"

.env

```

- Or you can open your bash terminal and type:

```bash title="bash"

echo ".env" >> .gitignore

```

!!! warning

    Navigate to your project's directory before typing command in the terminal

## Conclusion

- In conclusion, using `.gitignore` to ensure that all your environment variables you set in your `.env` file for the project is ignored when staging and pushing to version control.
- This helps all the sensitive datas such as port values or other configuration values will be hidden when deploying to different environments or teams.
