# passport-smartsheet

[Passport](http://passportjs.org/) strategy for authenticating with [Twitter](http://smartsheet.com/)
using the OAuth 1.0a API.

This module lets you authenticate using Twitter in your Node.js applications.
By plugging into Passport, Twitter authentication can be easily and
unobtrusively integrated into any application or framework that supports
[Connect](http://www.senchalabs.org/connect/)-style middleware, including
[Express](http://expressjs.com/).

## Install

    $ npm install passport-smartsheet

## Usage

#### Configure Strategy

    passport.use(new SmartsheetStrategy({
        clientID : SMARTSHEET_CLIENT_KEY,
        clientSecret: SMARTSHEET_CLIENT_SECRET,
        callbackURL: "http://127.0.0.1:3000/auth/smartsheet/callback"
      },
      function(token, tokenSecret, profile, done) {
        User.findOrCreate({ smartsheetId: profile.id }, function (err, user) {
          return done(err, user);
        });
      }
    ));

#### Authenticate Requests

Use `passport.authenticate()`, specifying the `'smartsheet'` strategy, to
authenticate requests.

For example, as route middleware in an [Express](http://expressjs.com/)
application:

    app.get('/auth/smartsheet',
      passport.authenticate('smartsheet'));

    app.get('/auth/smartsheet/callback',
      passport.authenticate('smartsheet', { failureRedirect: '/login' }),
      function(req, res) {
        // Successful authentication, redirect home.
        res.redirect('/');
      });

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2011-2013 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>
