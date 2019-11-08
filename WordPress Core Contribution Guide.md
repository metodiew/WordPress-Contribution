# WordPress Core Contribution Guide

## Agenda
* Contributing to WordPress
* Contributing to WordPress Core with code
* Trac
* Patches
* Version control
* Local Installation
* npm
* Contribute

## Some assumptions
* You have (basic) experience with localhost setup (Apache/Nginx/Other)
* You have (basic) knowledge of Version Control (Git/SVN)
* You have [npm](https://www.npmjs.com/get-npm) and Node.js setup (if not, it's time to setup)
* We'll need Grunt `npm install grunt -g` and `npm install -g grunt-cli`
* You have a WordPress.org profile

If some of these are not true, we'll get back to this a bit later and help you out!

## Contributing to WordPress
Let's start with some general [Contributing to WordPress](https://wordpress.org/support/article/contributing-to-wordpress/)

## Contribute with Code
Now we can move to [Contribute with Code](https://make.wordpress.org/core/handbook/contribute/)
Let's review the general page and get acquainted with the workflow

## Trac
History reasons

GitHub, at some point, maybe?

[https://core.trac.wordpress.org/](https://core.trac.wordpress.org/)

## Patches
We'll be working with patches, yeah!

[Working with Patches](https://make.wordpress.org/core/handbook/tutorials/working-with-patches/)

## The WordPress Codebase
[The WordPress Codebase](https://make.wordpress.org/core/handbook/contribute/codebase/)

## Version Control

### SVN
[The Code Repository (SVN)
](https://make.wordpress.org/core/handbook/contribute/svn/)

### Git
[The Code Repository (Git)
](https://make.wordpress.org/core/handbook/contribute/git/)

## Setup

### Docker
The official [WordPress develop repository](https://github.com/wordpress/wordpress-develop) suggest using Docker

### VVV
https://varyingvagrantvagrants.org

[Varying Vagrant Vagrants ( VVV )](https://github.com/Varying-Vagrant-Vagrants/VVV)

### Apache/Nginx

### Other options

## Apache (personal preference)

### hosts and local URL preparation
I have a custom local URL - [http://wpbleeding.local](http://wpbleeding.local)

`hosts` file
`127.0.0.1       wpbleeding.local`

My apache2.conf setup
```
# This is for WordPress Bleeding
<VirtualHost *:80>
	DocumentRoot /var/www/html/wpbleeding/src/
	ServerName wpbleeding.local
	ServerAlias wpbleeding.local
	 
	<Directory /var/www/html/wpbleeding/src/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>
````

### Database
wpbleeding, `utf8mb4_general_ci`
https://tinyurl.com/y6sgf8pj

### Clone the repo and setup the project locally
We'll be working with the Git version from GitHub
[https://github.com/WordPress/wordpress-develop](https://github.com/WordPress/wordpress-develop)

_I've used SVN for quite some time_ :)

### npm
We need to install the Package, using npm

For that reason, you'll need a few tools if you don't have them locally:  
* `npm install grunt -g` - [install Grunt](https://gruntjs.com/getting-started)
* `npm install -g grunt-cli`
* `npm install node-sass -g`
* these might need sudo access (not the best practice)

You might need at some point
`npm rebuild node-sass --force`

npm  
[https://i.imgflip.com/11e8zh.jpg](https://i.imgflip.com/11e8zh.jpg)

Now, we assume all of the npm packages you need are up and running. Let's install WordPress Core

### Let's install it

Navigate to the folder and clone the repository:  
`git clone git@github.com:WordPress/wordpress-develop.git wpbleeding`

_this will take some time, be patient_

We might need to fix file permissions for the folder

Open the local URL and we'll see [https://tinyurl.com/yyr5hqub](https://tinyurl.com/yyr5hqub)

Before running any build tasks you need to make sure the dependencies are installed. You can install these by running `npm install`.
_this will take some time_

The next step is to run  
`npm run dev`

This one will build the setup and you'll be able to install WordPress, following the standard steps.

Let's refresh the page, enter the database details

There you go! You have the WordPress development mode setup locally.

We are ready, let's contribute!

## Let's recap
* We saw Trac, Patches, how can we get involved
* We have setup a few npm packages we are going to need
* We have WordPress develop locally
* We should be ready

## A few things to keep in mind

### We are working in `src` folder

You can find more details here [Build tools: We’ve enabled running WordPress from /src again](https://make.wordpress.org/core/2018/12/24/build-tools-weve-enabled-running-wordpress-from-src-again/)

### A few gotchas  
`grunt watch --dev` - To build WordPress while developing

JavaScript files are placed in `/src/js/_enqueues/` directory.  
CSS Files are editable directly.

Developers can now run `grunt watch --dev` while working on JS files.
Once you are ready and need to build the JavaScript and CSS into `src` use `grunt build --dev` to automatically rebuild JavaScript and CSS files when their source is changed.
I suggest running this command when you are ready with your patch and you can prepare it for submitting.

Use branches for tickets
e.g. if you work on a ticket 1234, you can created a new branch `git checkout -b ticket-1234`

If you need to reset to the original stable state, run  
`git reset .` or reset each file/folder separately and run  
`grunt build --dev`
This will restore all JS/CSS files and all changes

## What's left?

### Find a ticket
[https://core.trac.wordpress.org/](https://core.trac.wordpress.org/)

[Good First Bugs for New Contributors](https://core.trac.wordpress.org/tickets/good-first-bugs)
* This does not need to be an easy patch - it can be a very well documented feature/bugreport/etc

### Work on a patch
You grat a ticket, work in it and you have the fix/update, nice! 

### Submit the patch to Trac
https://make.wordpress.org/core/handbook/contribute/git/#patches

### Testing others' patches is helpful!

### Writing tests

## Let's Contribute!
