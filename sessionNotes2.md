E2 P2 - TOPICS

1. How do we ignite out app
2. command to ignite the app
3. npx
4. Why are CDN links not a prefered way to bring React to our project?
5. Anouther way to get react into our app
6. Parcel Advantages (Superpowers)
7. Differential Bundling
8. How do we create a prod build?
9. Which are the three main files dist has?

How do we ignite our app - we will use parcel to ignite our app
We will use the following command

npx parcel index.html

index.html(As this is the source file of our project)

parcel has created a server - Server running at http://localhost:1234
This took 379ms to build it

- Now our app is hoisted on a server along with a port number

NPX

- Just like npm we have something as npx
- In npm we are just calling the command (used for installing a package)
- npx means executing our package

Ex: npx parcel index.html -> parcel goes to index.html and builds a development build and hosts that on the localhost:1234

Why are CDN links not a prefered way to bring React to our project?

- It is a costly operation
- We need to keep changing the CDN links
- It is not easy to maintain our package.json

\*\* Anouther way to get react into our app is via NPM
npm install react
Here we need react as a normal dependency and not as a development dependency

"dependencies": {
"react": "^18.2.0"
}

Similarly let us install react-dom
npm install/ i react-dom

"dependencies": {
"react": "^18.2.0",
"react-dom": "^18.2.0"
}

After running npx parcel index.html we still get the following error:

- Uncaught ReferenceError: React is not defined

Our code doesnt understand from where this react is coming from!
React.createElement in our App.js

Earlier this was coming from our CDN links
Now we need to get this from our node_modules

We will make use of the keyword 'import'
import React from "react"; -> This react refers to the react in our node_modules
import ReactDOM from "react-dom/client" -> This react-dom referes to the react-dom from our node_modules

we will still get the following errors:
@parcel/transformer-js: Browser scripts cannot have imports or exports.

<script src="./App.js"></script> treated as a normal JS file

We have to tell the browser this is not a normal JS file

<script type="module" src="./App.js"></script>

Parcel Advantages (Superpowers)

- Local server:
  Basically it creates a port and deploys our application in the server.

- Dev build:
  when parcel is executed, it generates the development build and stores inside the 'dist' folder,
  which we see in our browsers

- HMR (Hot Module Replacement)
  HMR or Hot Module Replacement is used to replace modules while the application is running without a full reload.
  It automatically refreshes the web when you only save your code. There is need to refresh the page.

- File watching algorithm:
  Monitors each and every folder for arrival of files.upon arrival it implements
  a certain process (written in c++)

- Image optimization
  Parcel supports resizing, converting, and optimizing images

- Caching
  It has faster builds

- Bundling

Differential Bundling
This helps in supporting old browsers (Older versions of IE, Chrome, etc)
Parcel gives different bundles for different browsers

How do we create a prod build?
we add the build keyword after parcel and before index.html
npx parcel build index.html

We get the following error:
"main": "App.js", Did you mean "App.html"?

the main in package.json is a way to tell npm this the entry point to the App.
In parcel, we provide the entry point as "npx parcel index.html"

parcel conflicts with this, we need to remove the main from package.json

ALL THE PRODUCTION BUILD GOES INSIDE THE "Dist" folder

When we execute parcel, it generates a development build and hosts it on the server (localhost:1234)
When it generates a development build, it puts it on the "Dist" folder

When we refresh our page, parcel uses the parcel-cache and dist folder (HMR)
When we do a production build, it is saved inside the "Dist" folder

The dist has three main files :-
(all files are compressed)

1. index.html
2. JS file
3. CSS file

From local we push the code to -> git <-> the server fetches from git and hosts it for the end user

The copy of node_modules is different in the local than what is present in the server

server will have package.json and package-lock.json

create-react-app does everything

BrowsersList
It is used configure our app to make it compatible with the older browsers
This needs to be configured in package.json file

"browserslist": [
"last 2 version"
]

We have created our OWN create-react-app
