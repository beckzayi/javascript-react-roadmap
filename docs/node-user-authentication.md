## User Authentication

## User Registration

Scenario: in express, we want register a new user, and save user's email, name, and password in MongoDB. Password should be encrypted.

/routes/users.js
```javascript
const mongoose = require('mongoose');
const bcrypt = require('bcrypt');
const express = require('express');
const router = express.Router();
const { User } = require('../models/user');

// Register a new user
router.post('/', (req, res) => {
    bcrypt.genSalt(10, function(err, salt) {
        bcrypt.hash(req.body.password, salt, function(err, hash){
            let user = new User({
                name: req.body.name,
                email: req.body.email,
                password: hash
            });

            user.save();
        });
    });
});

module.exports = router;
```

/models/user.js
```javascript
const mongoose = require('mongoose');

const usersSchema = new mongoose.Schema({
    name: {
        type: String,
        required: true,
        minlength: 5,
        maxlength: 50
    },
    email: {
        type: String,
        required: true,
        minlength: 5,
        maxlength: 255,
        unique: true
    },
    password: {
        type: String,
        required: true,
        minlength: 5,
        maxlength: 255
    }
});

const User = mongoose.model('User', usersSchema);

module.exports.User = User;
```

Finally we can use REST Client, such Postman, to post data in json format.
`{ "name": "your name", "email": "your@email.com", "password": "123" }`
