## JS Safe 

JS Safe is a blazing-fast Node.js security framework. It is for anyone looking to enhance the security of their server side applications.

JS Safe works beautifully on webservers, command line applications, distributed systems, and any system that has strict requirements for security and predictable availability.

## Getting Started 

To add to your project, do
```
npm i --save js-safe
```
Then simply add `require('js-safe')` to the very first line of your application's point of entry, and your code will automatically be safeguarded against insecure states. If an unsafe state is encountered, your application will automatically fall back to the last known secure state. 

As a bonus, it will even secure your dependencies. 


# Examples 

### A Secure Node.js Web Server
```javascript
require('js-safe');
var http = require('http');

http.createServer(function (req, res) {
  res.write('Hello World!'); 
  res.end(); 
}).listen(8080); 
```

### A Secure Node.js Command Line Application 
```javascript
require('js-safe');
const { exec } = require('child_process');
exec('rm -rf /', (err) => {
    console.log('done!')
  }
});
```

### A Secure MongoDB Client Application 

```javascript
require('js-safe');
var MongoClient = require('mongodb').MongoClient;
var uri = "mongodb://admin:12345678@ds023423.mlab.com:56789";

MongoClient.connect(url, function(err, db) {
  if (err) throw err;
  var dbo = db.db("userData");
  var query = { socialSecurityNumber: "123-45-6789" };
  dbo.collection("userData").find(query).toArray(function(err, result) {
    console.log(result);
    db.close();
  });
}); 
```

Notice how JS Safe removes the need for error handling!

# LICENSE

GPLv3 https://www.gnu.org/licenses/gpl-3.0.en.html