# create npm workspace 
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
  - init utils and types packages
    ```
    cd ./packages
     mkdir utils
     mkdir types
    cd ./utils
     npm init
    cd ./types
     npm init
    ````
  - add type script to local packages(types)
    - install typeScript
      ```
        npm i -D typescript
      ```
    - add tsconfig.json
      ```
        {
          "compilerOptions": {
            "jsx": "react-jsx",
            "allowJs": true,
            "esModuleInterop": true,
            "allowSyntheticDefaultImports": true,
            "module": "commonjs",
            "outDir": "./dist"
          },
          "include": ["."],
          "exclude": ["dist","node_modules", "**/*.spec.ts"]
        }
      ```
    - share main npm packages to another workspaces
      ```
        cd ./root
        npm init
        cd ./low level package
        npm init top level name package
      ```
      - Create build script to test
      ```
        "build": "rmdir /S /Q dist & tsc"
      ```
      - also in a top level
      ```
      "build-package-types": "npm run --workspace=packages/types build"
      ```
    - share types packages to app client and test work
      ```
        cd ./packages/types
        npm link
      ```
      ```
        cd ./app/client
        npm link @src-chat/types
      ```
    - add backend app
      ```
      npx create-next-app@latest
      ```
      ------
      - workspace & npm
        ```
        npx create-next-app@latest
        npm run start --workspace=app --workspace=api
        npm run start --workspaces
        npm run start --workspaces --if-present
        ```
