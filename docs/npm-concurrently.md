## npm run server and client concurrently

`{
    "scripts": {
        "client": "cd ./client && npm start",
        "server": "cd ./server && nodemon index.js",
        "dev": "concurrently --kill-ohters-on-fail \"npm run server\" \"npm run client\""
    },
    "devDependencies": {
        "concurrently": "^4.1.0",
        "nodemon": "^1.18.10"
    }
}`
