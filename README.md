# create nx workspace with different packages.json
  - create package.json file
      ```
    {"name": "src-chat",
    "version": "1.0.0",
    "description": "pet-project chat",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
     },
    "author": "Yaroslav Petriv",
    "license": "ISC"
    }
    ```
  - create .gitignore in console
    - echo > README.md

  - setup npm workspace 
    - add to package.json field
        ```
         "workspaces": ["apps/*, packages/*"]
        ```
  - add client app
    - use create react app
        ```
        npx create-react-app client --template typescript
        ```