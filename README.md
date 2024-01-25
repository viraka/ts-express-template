# Environment setup for a TS-Express Backend Codebase


1. **Open your terminal.**
2. **Navigate to your project directory.**
3. **Run `npm init -y` to create a `package.json` file with default values.**

4. **Install TypeScript and related dependencies:**
    ```bash
    npm install --save-dev typescript
    npm install --save-dev ts-node
    npm install --save-dev nodemon
    ```

5. **Install Expres,other dependencies and its type definitions:**
    ```bash
    npm i express body-parser cookie-parser compression cors
    npm i --save-dev  @types/express @types/body-parser @types/cookie-parser @types/compression @types/cors
    ```


6. **Create a `tsconfig.json` file:**
   - Run `npx tsc --init` or just create a new `tsconfig.json`.
   - Modify the generated `tsconfig.json` as required for your project.
        in this example we use:
        ```json
        {
            "compilerOptions": {
                "module": "NodeNext",
                "moduleResolution": "NodeNext",
                "baseUrl": "src",
                "outDir": "dist",
                "sourceMap": true,
                "noImplicitAny": true
            },
            "include": [
                "src/**/*"
            ]
        }
        ```
    <br>

7. **Setup `nodemon.json` file:**
    - Values are dependent on your project configuration:
        ```json
        {
            "watch": ["src"],
            "ext": ".ts,.js",
            "exec": "ts-node ./src/index.ts"
        }
        ```
8. **Set up your project structure:**
   - Create a `src` folder for your TypeScript files.
   - Inside `src`, create an `index.ts` file as your entry point.
   - Set npm start as `"nodemon"` in scripts key of the `package.json` file
    <br>
9. **Write a simple Express server in `index.ts`:**
    ```typescript
    import express from 'express';
    import http from 'http';
    import bodyParser from 'body-parser';
    import cookieParser from 'cookie-parser';
    import compression from 'compression';
    import cors from 'cors';

    const app = express();

    app.use(cors({
        credentials: true,
    }))

    app.use(compression());
    app.use(cookieParser());
    app.use(bodyParser.json());

    const server = http.createServer(app);

    server.listen(8080, () => {
        console.log('Server is running on port 8080');
    });
    ```
<br>

#####Reference used : [Code with Antonio](https://youtu.be/b8ZUb_Okxro)