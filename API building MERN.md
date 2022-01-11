## construct a Rest api in a MERN stack. 
- using [[node.js]] and [[MongoDB]]

Import package,
Execute it,

Create as many routes as needed

.get - retrieve somehtinhg

.post - send someithing

.delete

.patch - update

Route is an api endpoint

Middleware can be triggered when a type of route is hit
- this can implement authentication in this step 

Npm install mongoose
Moab good for testing api with a databases server setup 

Incoming json must be parsed, there is a package called body-parser

Const jsonparser = require('body-parser')

App.use(bodyParser.json())
Can use jsonparser as an object now. 

Post.find() returns all posts

MERN api with [[Jason Web Token]]