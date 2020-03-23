# Laravel Framework General Knowledge

## composer.json

At the root directory.

This file is the file that would basically hold your project's assets. 

`Composer` is dependency manager, but `composer` itself needs instructions.

And that's what this file is for.

A lot of this stuff, we'll never probably touch. 

We'll talk about how to add things to require, and things like that.

## Artisan 

Artisan is a command line tool that ships with laravel that allows you to do a ton of different things with your application. As a matter of fact, you can interact with your entire laravel application through artisan through something called tinker.

Run `php artisan` in terminal inside project's root directory.

This is going to output a bunch of differnet commands that are at your disposal.

Go all the way to the top where it says `Available commands:`.

And we can consider these **the root level commands** that you have. So these commands, you only run with `php artisan`. After that, they are basically  namespaced commands you can run, like in the `app` name space, you have `app:name`, `auth`, `auth:clear-resets`, and so on, and so forth. Now it may seem super-overwhelming that there is all this stuff at your disposal, but no worries again, just one thing at a time.

The very first thing I want to talk about is *authorization*.

One of the reasons to use a framework like *laravel* is to basically rocket your development into developing exactly what you need for your application, as opposed to spending time, developing things you don't quite need.

So, we're going to be talking about `make:auth`. But, before this, how do we actually view this page in our browser?

Well, actually, that's quite simple.

Laravel ships with a built-in php server, that we can use.

Use this command right here: `php artisan serve`.

---

So where would you find anything related to HTML? 

`resources/views/welcome.blade.php`

`blade` is a rendering template, and what it will allow you to do, is throw in snippets of php in your views. Without it feeling like you are hacking away at your views, because your views will primarily be composed of HTML markup. There should be no reason why you should *never be computing or fetching database queries or anything like that in your views*. That's what your *controllers* are for. We'll get to that.

---

Laravel ships with an authentication system that allows you to register users, and allows you to login users, keeps track of all your sessions. it does all of this for you out of the box.

Now this command, even though it is a little early to introduce you to it, we have to run it, because it will change your views, meaning it will change this page that we're working with.

`php artisan make:auth`

### For Laravel >=6, run the following commands. make:auth is no longer available

```
composer require laravel/ui
php artisan ui vue --auth
```

This will create lots of new things in the view folder that is needed for authentication, such as *login* and *register*.

---

## Laravel is a full-development framework

Meaning it does have opinions about frontend just as much as it does about backend.

Laravel ships with a working implementation of `bootstrap` (twitter bootstrap) and `Vue.js`.

However, we do need to run a compilation.

Frontend: `HTML`, a little bit of `JavaScript`, and `Vue.js`

Backend: `PHP`

---

If you're more familiar with things like `jquery` or `React.js`, or anything like that, there are ways to switch out of `vue.js` and rip everything out and start over with `jquery` or any other framework in the `JavaScript` world that you would want to use. So don't worry about the fact that `Vue.js` is what it ships with. You of course have the possibility of changing that out and doing exactly what you want to do.

---

NPM in the frontend development is one of those things you need to compile before you can use. To run a compilation, `npm run dev`.

What this is going to do, is take everything that Laravel ships with, and it will compile it down to a file that we can actually use.

The reason for doing this through `webpack` is that `webpack` is able to take all of this code you are going to bring in through JavaScript and we are talking about quite a significant amount of code, and then its going to compile all down to the smallest, minified file that you can find.

Now you may be used to just pulling in some packages through a script, but remember, in a framework we kind of want to follow all of the best practices.

---

What we've now done is we now have this `app.css` and `app.js`. So Larvel has compiled all of our frontend assets into these two files. Obviously one for javascript, and one for CSS.

Incorrect Directory: `resources/js/app.js`

Correct Directory: `public/js/app.js` & `public/css/app.css`

You'll see that this file is not your regular javascript file.

A lot fo magic happened to this file. And it is not your typical file. You would never touch this file directly.

The one you'll be working with is the one inside `resources` directory.

Compiled files always end up inside this `public` directory.

---

# Now on to setting up Database

`php artisan`

## Migrations

migrations are files that describe your database.

So instead of you going into the database and making a bunch of changes to it, and then you having to going to your production server, and make those same changes manually, you are going to write these migration files that are going to describe your database.

now this is a little bit of a higher concept, but just think of migrations as a file that holds all the instructions that you need to tell your database to create itself. And so throughout this project, we're going to modify the database, but through the migrations, not directly into the database.

Now why would you do it this way? The answer is fairly simple. It describes each change in a very systematic way. If you were to go into your database and make some changes unless you document those very very well, more then likely you're going to forget to run a step or two in your production and everything blows up. Furthermore, any other developers working with you are not going to know how to recreate that change.

And so that is not create for teams. 

So things like migrations are one of those integral parts of working in a team, because it allows everybody to have the same definition of what the database is supposed to look like.

In order for us to run this migrate command, we need to set up some sort of database with Laravel.

---

## SQLite

Create a file and this file is going to be a flat-file database file. That's how SQLLite works.

```
// .env
DB_CONNECTION=sqlite

// erase everything else that starts with "DB_"
```
>TIP: if you make any changes to .env file, make sure to stop the server from running and restart for it to work without any errors

How do we actually get the database migrated? How do we get the latest state possible?

`php artisan migrate`

This should create users table & password resets table.

---

In order to add a new field in `register` such as `username`, we have to look at what `make auth` actually added to our files.

Go to `/views/auth` directory's `register.blade.php`
