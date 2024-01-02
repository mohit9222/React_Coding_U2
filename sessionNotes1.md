/** Igniting our App **/

E2 P1 - TOPICS

- It is good practice to create a README.md file
- What does Igniting our app mean /Things to do before production
- what does a create react app create
- Does react alone make our app fast?
- NPM
- using NPM in our project
- package.json
- Most important package in our App
- Types of Bundlers
- what is parcel bundler
- how do we install the dependencies
- What is caret(^) and Tilda(~)
- Difference between package.json and package-lock.json?
- what is integrity in package-lock.json?
- node_modules
- TRANSITIVE DEPENDENCIES
- In our project how many package.json files are there?
- Do we need to push our node_modules to production / GitHub?
- Do we need to push our package.json and package-lock.json to GitHub?

- What does Igniting our app mean?
  Things to do before production:

1. Bundling
2. Code Spliting
3. Chunking
4. Image Optimiztion
5. Remove comments
6. Minify the code
7. Need to compress the code

when we do a create react app it creates a scaffold (gives a react app which is already production ready)

How we can create our own create react app

- Does react alone make our app fast?
  No, React makes our app fast upto an extent, but there are other library's, packages which contribute in making our app
  faster.

NPM (Manages Packages)

- NPM does not stand for - Node Package Manager(NPM)
- It doesnt have a full form
- Link - https://www.npmjs.com/
- Behind the scenes it works as Node Package Manager (Manages Packages)
- It is a standard repository for all the packages
- All our packages, libraries, utilities are hosted in NPM (Manges our project)

using NPM in our project
npm init

- This will ask a couple of questions

package name: react-learning
version: (1.0.0)
description: Learning React in Detail
entry point: App.js
test command: jest
git repository:
keywords: react, redux, front end
author: Mohit R Chugh
license: (ISC)

Ignores a few packages
npm init -y

- A new file is created - package.json

A configuration for our npm
keeps a track of all the packages in our code

What do we need package.json?
NPM manages all our packages which we install in our system, this is also called as dependencies

- Most important package in our App!

BUNDLER - It bundles/packages our app which needs to be shipped to production

- HTML, CSS, JS need to be bundled to production
- Types of bundlers :

1. Webpack
2. Parcel
3. Vite

create-react-app (uses webpack and babel)

PARCEL BUNDLER

- Comes as a Node Package
- Any dependency / package needs to installed the following way:
- Syntax: npm install <dependency-name>

// We are telling npm that we need parcel in a dev dependency and not in a normal dependency

- npm install -D parcel (D -> stands for development dependency)

- There are two types of dependencies :
  1. DEV Dependency (Required during development phase)
  2. Normal Dependency (Used in production phase)

PARCEL is a BEAST

Once we install parcel you will see in package.json
"devDependencies": {
"parcel": "^2.10.3"
}

what is caret(^) and Tilda(~) in package.json?

- Caret(^) - It is usually used to specify a range that allows for both minor and patch
  updates.
- Example: parcel: “^1.2.3” < "2.0.0" —> We can have any major version 1 and equal to the
  minor versions i.e 1.3.0, 1.4.0 but not 2.0.0.
- Tilda (~) - It is usually used to specify the range that allows patch updates. Tilda is
  usually for patch updates and not for any breaking changes.
- Example: parcel: “~1.2.3” < "~1.3.0"> —> 1.2.4, 1.2.5, 1.2.6 etc but cannot have 1.3.0.
- It is generally better to use caret(^) over tilda(~)
- major.minor.patch ("1.2.3)

Difference between package.json and package-lock.json?
Package.json - keeps a track of the approx. version of all our packages
Package-lock.json - Keeps a track of the exact version of all our packages

In our package-lock.json we have something called as integrity: Is a sha512 hash
Keeps a hash to verify whatever is there in the local environment (local machine) is the same version deployed in production

- node_modules (Collection of packages/dependencies)

Contains all the code we fetched from npm
-> Something like a database for our packages required by our project
Our project has dependencies -> parcel has its own dependencies -> Those dependencies have their own dependencies -> ....
This is known as TRANSITIVE DEPENDENCIES

In our project how many package.json files are there?

- There is more than 1 package.json in our app because each of the packages in node_modules have their own dependcies and package.json
- Each of the package maintains its own configuration and dependency

Do we need to push our node_modules to production / GitHub?

- No, we dont need to push our node_module to production or Github
- The best practice is to create a .gitignore file (If we dont want to push anything to production / git, then we add it in this file)

Do we need to push our package.json and package-lock.json to GitHub?

- YES, both these files maintains a note of what all dependencies our project needs
- If we have these two files, we can re-create our node_modules (even if it is deleted)
