# What is this repository

My replication of [a tutorial series by Ben Awad on YouTube](https://www.youtube.com/watch?v=G8KXFWftCg0&list=PLN3n1USn4xll1d97ZtIk2t7UpSxWGdIn5).

## How to reproduce (i.e. running summary of Ben's videos)

1. Create a new folder.
2. Create a `package.json` file
3. Set private to true (`"private": true`), and add an array of workspaces (in the tutorial - "common" and "server") to the package.json file: (`"workspaces": [ "common", "server" ]`).
4. Create the package folders (`mkdir ./common && mkdir ./server`).
5. Run `yarn init -y` in each folder.
6. Create `./common/index.js` file and export a function from it.
7. Create `./server/index.js` file and import the common function (using the name provided in the root package.json):
    * i.e. `const commonFunction = require("common")`
8. Add "common": "1.0.0" as a dependency for "server" (`"dependencies": { "common": "1.0.0" }`).
9. Run `yarn install` from the "server" directory".
    * This will add a node_module root directory which will contain simlinks to both packages - allowing them to call each other as if they were external packages.
10. Run `node ./server/index.js` to confirm this works :).
11. Rename packages to the conventional naming structure: `@project/common` and `@project/server`.
    * Make sure you rename package.json names, import and the dependency entry.
    * After renaming, remember to run `yarn install` again to update these names in code.
    * Confirm all is good by running `node ./server/index.js` again.
