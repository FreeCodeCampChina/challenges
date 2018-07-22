# Introduction to Information Security with HelmetJS Challenges #

HelmetJS is a type of middleware for Express-based applications that automatically sets HTTP headers to prevent sensitive information from unintentially being passed between the server and client. While HelmetJS does not account for all situations, it does include support for common ones like Content Security Policy, XSS Filtering, and HTTP Strict Transport Security, among others. HelmetJS can be installed on an Express project from npm, after which each layer of protection can be configured to best fit the project.

Working on these challenges will involve you writing your code on Glitch on our starter project. After completing each challenge you can copy your public glitch url (to the homepage of your app) into the challenge screen to test it! Optionally you may choose to write your project on another platform but it must be publicaly visible for our testing.
Start this project on Glitch using this link or clone this repository on GitHub! If you use Glitch, remember to save the link to your project somewhere safe!

# Upcoming Lessons #

Install and Require Helmet

Hide Potentially Dangerous Information Using helmet.hidePoweredBy()

Mitigate the Risk of Clickjacking with helmet.frameguard()

Mitigate the Risk of Cross Site Scripting (XSS) Attacks with helmet.xssFilter()

Avoid Inferring the Response MIME Type with helmet.noSniff()

Prevent IE from Opening Untrusted HTML with helmet.ieNoOpen()

Ask Browsers to Access Your Site via HTTPS Only with helmet.hsts()

Disable DNS Prefetching with helmet.dnsPrefetchControl()

Disable Client-Side Caching with helmet.noCache()

Set a Content Security Policy with helmet.contentSecurityPolicy()

Configure Helmet Using the ‘parent’ helmet() Middleware

Understand BCrypt Hashes

Hash and Compare Passwords Asynchronously

Hash and Compare Passwords Synchronously