
# Middlewares

A middleware is a function that sits between an incoming HTTP request and the final route handler (or next middleware). 

It can:
- modify req and res
- end the request (send a response)
- call next() to pass control to the next middleware/handler
- call next(err) to pass an error to the error-handler middleware

Normal Middleware

        function helper(req,res,next){ 
            console.log(req.method,req.url);
            next();
        }

Error handling Middleware

        function helper(err,req,res,next){
            console.error(err);
            res.status(500).json({error: 'Something broke'});
        }

## Types of middleware

### Application-level 
- Attached to app and run for all matching requests.

        app.use(helper); // runs for every request


### Router-level 
- Attached to an express.Router() and run for routes on that router.

        const router=express.Router();
        router.use(helper); // runs only for router routes


### Route-level 
- Passed directly to a route and runs only for that route.

        app.get('/private', auth, (req,res)=>res.send('ok'));


### Built-in 
### Third-party 
### Error-handling 

## Common real-world middleware uses

- Logging (morgan)
- Body parsing 

        express.json()
        express.urlencoded()

- Cookie parsing (cookie-parser)

- CORS (cors)

- Security headers (helmet)

- Rate limiting (express-rate-limit)

- Compression (compression)

- File upload parsing (multer,busboy)

- Authentication (JWT,session guards)

- Validation (Joi,express-validator)



