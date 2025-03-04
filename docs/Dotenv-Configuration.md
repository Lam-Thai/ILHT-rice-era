# Configuration and Setup

## Overview

In this section, you will learn how to configure **_dotenv_** to your express application. This is the foundation for all enviroment variable management in your future projects as it will allow you to safely share your code with others, or on GitHub.

### Configuration steps for Dotenv setup

1.  Open up your selected project and make sure you are in its directory

    ```title="inside your terminal" linenums="1"
    cd <your project directory>
    ```

2.  Create a _**.env**_ at the root of your project directory.

    - Placing your _**.env**_ file at the root directory ensures that other developers can quickly access and use the environment variables

    !!! warning

        Never commit your _**.env**_ file to GitHub, preventing this will be covered in a later section. For now, create a _**.env.example**_ to ensure that developers will know what environment variables is needed for the project without compromising your data _(.env.example will be committed)_.

    ![](/assets/configuration_screenshot1.png)

3.  Import Dotenv into all the scripts that have data that needs to be hidden

    - Since this guide is using Typescript, use the _import type statements_ , this way you obtain the type information for the module.

    - Call the configuration function to read the contents of your .env file which parses its contents, making it available to all scripts or files that include the import.

    ```title="example.ts" linenums="1"
    import dotenv from "dotenv"
    dotenv.config();

    ```

## The location of the variables

- When you call the configuration
  function in your Typescript file(s), all the variables that you stored in your .env file will assigned inside an object called **process.env**

- This will load your environment variables from _**.env**_ into your project's root directory

- In the next task, you will learn how to access your environment variables using the **process.env** object

## Inserting data into _**.env**_

Once you created your .env file(s), you can insert your variables following the syntax below:

- In your _**.env**_ file:

```title=".env" linenums="1"
 YOUR_ENVIRONMENT_VARIABLE="<insert data here>"

```

!!! info

    When naming your environment variables, make sure that you are replacing all your whitespaces with underscores ( _ ) and the name is all upper case. This is that you can differinciate between variables in your code and your _**.env**_ file
