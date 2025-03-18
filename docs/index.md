# Home

## Introduction

Dotenv is a library that allows software developers to conceal their
sensitive data within their code by keeping it in a _**.env**_ file. This tool can be used for Database connections,
API authentication, Security, and making your code
more secure and reliable.

In this documentation, you will learn how to secure and protect your web applications to prevent any attackers attempting to steal user information or break your web application.

## Intended Users

- Intermediate level developers who need to protect the sensitive data in the server.
- Software development teams working on web-applications that need data security.

## User Specification

Users that want to follow this guide must be proficient in the following:

- `Express using Typescript or Javascript` - Must be proficient in creating and understanding express routes to develop websites.
- `Authentication` - Must be comfortable developing authentication features including hashing a user's password and cookie-session.
- `Github Repository terms and conditions` - Must know what code GitHub tolerates to prevent getting repositories flagged and taken down.
- `using .gitignore` - Knowledge of hiding certain files from the git repository using a .gitignore file.

## Software Requirements

Before proceeding, ensure you have the following installed:

- [TypeScript](https://www.typescriptlang.org/) v5.x or later

- [JavaScript](https://javascript.info/) ES6 or later

- [Visual Studio Code](https://code.visualstudio.com/)

- [DotEnv](https://www.npmjs.com/package/dotenv) v16.x or later

- [Express.js](https://expressjs.com) version 4.18.12 or later

## Procedures Overview

- [Dotenv Configuration](Dotenv-Configuration.md)
- [Hiding your server PORT](port.md)
- [Hiding Secret Keys](secrets.md)
- [Using .gitignore](gitignore.md)

## Notes and Warning Messages

Throughout the documentation, we will use message blocks to alert you to relevant information. Each possible message block, from most important to least important:

!!! info

    Indicates additional information or tips.

!!! success

    Indicates what success looks like.

!!! warning

    Specifies content that must be read before proceeding.

!!! danger

    Specifies actions that may cause an error or will cause the application to crash.
