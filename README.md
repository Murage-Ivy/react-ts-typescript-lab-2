# Setting Up a TypeScript Directory

## Learning Goals 

- Configure a directory to utilize TypeScript
- Get set up for the following lessons

## Introduction

In this assignment, we'll be initializing this lab's directory to use TypeScript.
You will continue to use this directory to code along and practice during lessons 
for the remainder of the TypeScript section. 

> **Note**: You will not be doing other labs in this directory, those will still
> have their own directories for you to clone down and work in. 

## Instructions

1. Fork this repo and clone it down onto your machine. 
2. Initialize the repo as a TypeScript project using the `tsc --init` command.
3. Create two sub-folders, named `src` and `dist`. 
4. Open up the `tsconfig.json` file generated when we initialized
   the directory in step 2.
5. Replace it with the following, simplified configuration: 

```json
{
  "compilerOptions": {
    "target": "es2016" /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */,
    "experimentalDecorators": true /* Enable experimental support for TC39 stage 2 draft decorators. */,
    "module": "commonjs" /* Specify what module code is generated. */,
    "rootDir": "./src" /* Specify the root folder within your source files. */,
    "outDir": "./dist",
    "esModuleInterop": true /* Emit additional JavaScript to ease support for importing CommonJS modules. This enables 'allowSyntheticDefaultImports' for type compatibility. */,
    "forceConsistentCasingInFileNames": true /* Ensure that casing is correct in imports. */,
    "strict": true /* Enable all strict type-checking options. */,
    "skipLibCheck": true /* Skip type checking all .d.ts files. */
  },
  "include": ["src/**/*", "test/**/*"]
}
```

You're now setup to utilize TypeScript's very helpful watch mode in this directory!

Before we move on, take a closer look at the simplified `tsconfig.json` we provided. 
In it, we've specified the `rootDir` as `src` and the `outDir` as `dist`. This means 
we want all our `.ts` files to be within `src` and all the compiled `.js` files will be 
generated inside `dist`.

## Test Our Setup 

Let's test and make sure our configuration works correctly. Create a file called `test.ts`
in the `src` folder and write a simple line of code, such as `console.log('Hello world!')`. 

In terminal, turn on TypeScript's watch mode with `tsc -w`. If all is well, we should not 
get any errors and we should see a file generated in the `dist` folder called `test.js`. 
Great, the set up works! 

## Run Compiled Code 

The last thing to cover is how to now run the compiled code. As we did before, we can 
simply run `node <compiled JS filename>`. Try it now with `node dist/test.js`. 

While that works perfectly fine, we have to run that line every time we want to 
test the compiled code. Thankfully, there is a Node equivalent to TypeScript's watch 
mode called `nodemon`. Similar to watch mode, `nodemon` re-runs a specified file when 
it detects a change has been made to it. 

> **Note**: There are ways to make `nodemon` watch multiple files at once, but that is 
> beyond the scope of our lessons at the moment. For our purposes, watching one file 
> at a time will suffice. 

How do we get `nodemon`? Like TypeScript's `tsc` command, it is available as a package
on npm. If you don't already have it installed, install it globally with `npm i -g nodemon`. 

Using it is very similar to the `node <filename>` command we're familiar with. We simply 
replace `node` with `nodemon`. For example, to watch the `test.js` file, we would use:

`nodemon dist/test.js` 

Now, any time `test.js` gets recompiled, nodemon will re-run the file with the newly 
compiled code. 

To stop `nodemon` from watching when we're done developing, we exit the same way we exit 
TypeScript's watch mode: `Ctrl + C` 

With that, we are now fully set up to start practicing more TypeScript features! 