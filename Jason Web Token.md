## JWT and route notes
Brightness 30 on monitor

## project structure
Npm init <- this creates paackage.json
package.json, contains all packages which need to be downloaded from the internet 

__Now for imports, js equivalent is const express = require('express')__



Jason Web Token, JWT for short

Install list

Express for routes

Nodemon to restart server

Index.js
Define server 

Listen(port, console.log(display message))

Authentication is implemented as a route which can be imported

(They will function as middleware's)

## implementation planning 
Will generate JWT token once a user registers or logs in

JWT expires 20 minutes after creation or 20 minutes after last operation

#### Password validation
Package: @hapi/joi
Make schema, validate user data with joi schema: Joi.validate(req.body, schema
Proceed with normal user registration

#### Password hashing @43min
Package: bcryptjs
	Generate a salt: hash password during registration with bcryptjs salt
its Best practice to not send the hashed password back after registering/logging in as confirmation 

Login: check hash against password user is sending to log in, using bcyrpt.compare 

#### JWT @ 01:00:25
Add in after verifying correct user id/pass in login
Import jsonwebtoken
Create a token secret in env file, can be any random string
Create token using JWT.sign, assign res.header the token
##### adding middleware route to check authorization using jwt (this is extensible)
JWT.io to check valid encoding for token
@1:04:00

401 status is resource denied due to permission, auth-token is how you can access jwt token in json res header in request

Test if jwt token is present, then check if valid

