#node-stopforumspam

--> build status

Helps weed out spam accounts during signups.  Allows you to check usernames, emails and/or ip addresses against stopforumspam.com API.

## Installation
    npm install spamcheck

## Examples

### Use in registration page
```javascript
var sfs = require('../lib/util/stopforumspam');  // get our object

// call checkspammer with any mixture of the following properties in the object to check: ['username', 'email', 'password']
sfs.checkSpammer({ip: req.connection.remoteAddress, email: req.body.email}, function(err, isSpammer) {
  if (err) console.log(err);
  
  if (isSpammer) {
    // user is spam, send back a custom status code with nice message or our spammer.
    res.send(452, 'You are listed as a spammer and registration will not continue.');
  } else {  
    // user is not spam, register the user.
    
    // insert into the db, etc.
  }
});

```

## Help
Please visit the stopforumspam.com API documenation to fully understand the way this works.

### [StopForumSpam.com API](http://www.stopforumspam.com/usage)

## Notes
StopForumSpam.com will allow up to 20,000 API requests daily.  If you need more, please see their database page.  They provide hourly updates to their database that you can
download and work with directly and locally.

### [StopForumSpam.com API](http://www.stopforumspam.com/downloads/)
