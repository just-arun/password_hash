# password_hash

## instalation
```npm
$ npm i -s bcryptjs
```

## Usage - Sync
To hash a password:
```js
var bcrypt = require('bcryptjs');
var salt = bcrypt.genSaltSync(10);
var hash = bcrypt.hashSync("B4c0/\/", salt);
// Store hash in your password DB.
```
### To check a password:

```js
// Load hash from your password DB.
bcrypt.compareSync("B4c0/\/", hash); // true
bcrypt.compareSync("not_bacon", hash); // false
```
### Auto-gen a salt and hash:
```js
var hash = bcrypt.hashSync('bacon', 8);
```

## Usage - Async
### To hash a password:
```js
var bcrypt = require('bcryptjs');
bcrypt.genSalt(10, function(err, salt) {
    bcrypt.hash("B4c0/\/", salt, function(err, hash) {
        // Store hash in your password DB.
    });
});
```
### To check a password:
```js
// Load hash from your password DB.
bcrypt.compare("B4c0/\/", hash, function(err, res) {
    // res === true
});
bcrypt.compare("not_bacon", hash, function(err, res) {
    // res === false
});
 
// As of bcryptjs 2.4.0, compare returns a promise if callback is omitted:
bcrypt.compare("B4c0/\/", hash).then((res) => {
    // res === true
});
```

## Auto-gen a salt and hash:
```js
bcrypt.hash('bacon', 8, function(err, hash) {
});
```




