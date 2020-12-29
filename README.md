# 31.0-node

- Servers
    - a ***server*** can be any program or device that provides functionality for other programs or devices, called ***clients***
        - every time you visit a website or use a web application, you're making a request to a server and your browser is the client
    - the job of the server is to respond with client requests
        - this is the 'contract' between servers and clients: when a client makes a request, the server must respond, even if the response is that it can't perform the job that was requested
        - this request-response paradigm is referred to as the ***HTTP request-response cycle***
- Node

    ## Working with Modules and Dependencies

    - dependencies are modules or libraries of code, separate from out application, that our application relies on in order to function
        - its an easy way to reuse code, either written by ourselves or someone else
    - usually all info is inside the package.json module
    - node modules always go inside .gitignore

    ### Create a project

    1. create a new package.json

        ```jsx
        // inside terminal
        npm init -y
        ```

        - -y means it will use default options

    2. install lodash

        ```jsx
        // inside terminal
        npm install lodash
        ```

        - creates node modules
        - info can be found in ***lodash.js*** (if curious)
    3. make sure that node modules files are not being tracked
        1. set up a new git project in this directory

            ```jsx
            // inside terminal (specifically inside directory)
            git init
            ```

        2. create a file called .gitignore in the root of your project directory

            ```jsx
            // inside terminal (specifically inside directory)
            touch .gitignore
            ```

        3. Open ***.gitignore*** and type node_modules into it
    4. create a new variable of lowdash and tell the program that it needs to require lodash modules

        ```jsx
        const _ = require("lodash");
        ```

    5. create a new file and then import and export that file
        - new file needs lowdash requirement a the top and export at the bottom

            ```jsx
            // begins with
            const _ = require("lodash");

            //ends with
            module.exports = stuff;

            // stuff is whatever you want to export
            //  in class example it was an arry but this will be updated soon with
            //all options
            ```

        - index.js file needs an import of the file that is being used

            ```jsx
            const bears = require('./path to file')
            ```

    6. now that reference will be accessible inside the ***index.js*** file

    ## Working with the File System

    1. Set up
        1. Create a new folder in your `sandbox` directory, call it `node-fs`
        2. `cd` into `node-fs` and create a file called `index.js`

    ### Write to a file

    ```jsx
    // first argument is the path of the new file we are creating
    // second argument is what will be in the file
    // third argument is a callback function that displays the error
    fs.writeFile('./file.txt,', 'hello world', (err) => {
      if(err) {
        console.log(err)
      } else {console.log('done')}
    })
    ```

    ### Read From a File

    ```jsx
    // first argument is the path of the file we are reading
    // second argument
    // fs.readFile("./file.txt", "utf8", (err, data) => {
    //   if (err) {
    //     console.error(err);
    //   } else {
    //     console.log(data);
    //   }
    // });

    //  be careful with commenting out things
    //    if new content is written in path file of old content it will be overwritten

    const pojo = {
      animal: false,
      name: "peter obvarious jones otlewski",
      password: "shenanigan174",
      hobbies: ["reading", "writing", "snowboarding", "cat petting"]
    };

    // this JSON method we are using is built into node
    // this turns a regular javascript object into json
    const pojoJson = JSON.stringify(pojo)

    console.log(pojoJson)

    fs.writeFile('./file.txt,', pojoJson, (err) => {
      if (err) {
        console.log(err)
      } else {
        console.log('done')
      }
    })
    ```
