# Wishlist

The goal of this project is to provide dedicated shopping and wishlists for registered nextcloud users in a quick and easy way.

A private delayed shopping list for items, you don't need right now or my want to spend some time to think about, e.g. if you really want to spend the money on them.
A public wishlist to make the life easy for friends and family just around your birthday or the holydays.
Projects related shopping lists, that serve to collect all needed items before the final purchase
Or maybe a list of cool items you don't have the money for at the moment.

### Features

Other than using notes, tasks or other existing nextcloud projects for this purpose, this app should include features like:

* sharing lists with other registered users (e.g. as a collaborative shopping list for a move)
* publishing lists and list items for non registered users. (e.g. as a wishlist)
* a "pick as gift" function for non registered users. (to temporary hide or mark wishlist items as "as gift selected" to avoid duplicate gifts)
* a simple method to add list items by only prividing webshop links with:
    * automatic parsing of product details like price, image, description, availability, ... (where possible)
    * periodic check of reachability/ availability of list items
    * integration of well known shops like Amazon, Etsy, ... (for e.g. price tracking, availability notification, ...)
* a dedicated Android app to be able to add list items by sharing links from a browser

## Contribution

If you would like to contribute, there are ample oppertunities to do so.

* you found a bug?
* there is a feature missing?
* you have an idea to improve the user experience?
 --> open an issue

* you can code
 --> fork this project and code away, but please don't forget to issue a pull request
 
Thanks a lot, I realy appreciate the help.

## Installation

Place this app in **nextcloud/apps/**

### Dev Setup

See https://docs.nextcloud.com/server/latest/developer_manual/app_development/tutorial.html#setup

## Building the app

The app can be built by using the provided Makefile by running:

    make

This requires the following things to be present:
* make
* which
* tar: for building the archive
* curl: used if phpunit and composer are not installed to fetch them from the web
* npm: for building and testing everything JS, only required if a package.json is placed inside the **js/** folder

The make command will install or update Composer dependencies if a composer.json is present and also **npm run build** if a package.json is present in the **js/** folder. The npm **build** script should use local paths for build systems and package managers, so people that simply want to build the app won't need to install npm libraries globally, e.g.:

**package.json**:
```json
"scripts": {
    "test": "node node_modules/gulp-cli/bin/gulp.js karma",
    "prebuild": "npm install && node_modules/bower/bin/bower install && node_modules/bower/bin/bower update",
    "build": "node node_modules/gulp-cli/bin/gulp.js"
}
```


## Publish to App Store

First get an account for the [App Store](http://apps.nextcloud.com/) then run:

    make && make appstore

The archive is located in build/artifacts/appstore and can then be uploaded to the App Store.

## Running tests
You can use the provided Makefile to run all tests by using:

    make test

This will run the PHP unit and integration tests and if a package.json is present in the **js/** folder will execute **npm run test**

Of course you can also install [PHPUnit](http://phpunit.de/getting-started.html) and use the configurations directly:

    phpunit -c phpunit.xml

or:

    phpunit -c phpunit.integration.xml

for integration tests
