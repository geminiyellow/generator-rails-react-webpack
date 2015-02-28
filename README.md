# generator-rails-react-webpack

> [Yeoman](http://yeoman.io) generator

[![NPM](https://nodei.co/npm/generator-rails-react-webpack.png?downloads=true)](https://nodei.co/npm/generator-rails-react-webpack/)

## Getting Started

To install `generator-rails-react-webpack` from npm, run:

```bash
$ npm install -g generator-rails-react-webpack
```

## Up and Running

Create Ruby on Rails project with normal `rails` command, but skip gem bundling:

```bash
$ rails new app-name --skip-bundle
```

Then, initiate the generator:

```bash
$ cd app-name
$ yo rails-react-webpack
```

Answer 'Yes' to all 'Overwrite' actions. Then, update 'config/database.yml' if you use different database than 'sqlite3'.

## Dependencies

- [Bower](http://bower.io/) via `npm install -g bower`

## Application template

### javascript modules

All javascript modules are placed in 'app/frontend/javascripts' folder, which will be compiled into 'app/assets/javascript/build'
folder. 'app/assets/javascript/build' is also ignored in `.gitignore` which I will explain in [config/webpack](#webpack).

### package.json

Manage dependencies for javascript modules with incremental rebuilding for each module.

### webpack

- `config.json` is responsible for storing application configuration. In addition, you can set up any extra configurations
  here, which will be loaded into `javascript-build.js` via `config = require('./config.json');`
- `default.config.js` contains the basic webpack settings for both development and production environment.


### Current transformation applied

- [babel-loader](https://github.com/babel/babel-loader)
- [expose-loader](https://github.com/webpack/expose-loader)
- [imports-loader](https://github.com/webpack/imports-loader)
- [exports-loader](https://github.com/webpack/exports-loader)

### Available gulp task

```bash
$ guld javascript:clean # remove the build folder placed at 'app/assets/javascripts/build'
$ guld javascript:dev # watch over changes for multiple js bundle
$ guld javascript:build # build for production
```

## Start developing

Run these commands, and start coding

```bash
$ gulp javascript:dev
```

```bash
$ rails server
```

## Assets compile
Compile your assets before deploying to production server

```bash
$ gulp javascript:build
$ rake assets:precompile RAILS_ENV=production
```

## Options

Name: mongoid (for mongodb)

add `--skip-active-record` option to your `rails new app --skip-active-record` command before selecting this option.

## Task

### Live reload

For using livereload utility, firstly, install [guard](https://github.com/guard/guard-livereload). Then, use [rack-livereload](https://github.com/johnbintz/rack-livereload)
or install [LiveReload Safari/Chrome extension](http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-)

## Testing
Comming up

```bash
$ bundle exec guard # to run the guard server and enjoy coding
```
## Structure

```
application/
  |- app/
  |  |- assets/
  |  |  |- images/
  |  |  |- javascripts/
  |  |  |  |- build/
  |  |  |  |  |- page-module.bundle.js
  |  |  |  |- application.js
  |  |- frontend/
  |  |  |- javascripts/
  |  |  |  |- <page-module-dependencies>/
  |  |  |  |- <page-module>.bundle.js
  |  |  |- stylesheets/
  |  |  |  |- application.css
  |  |- controllers/
  |  |- helpers/
  |  |- mailers/
  |  |- models/
  |  |- views/
  |  |  |- application/
  |  |  |  |- index.html # default template for the application
  |  |  |- layouts/
  |  |  |  |- application.html.erb
  |- bin/
  |- config/
  |  |- browserify/
  |  |  |- config.json
  |  |  |- errors-handler.js
  |  |  |- javascript-build.js
  |  |- initializers/
  |  |  |- bower_rails.rb # bower rails config
  |- db/
  |- lib/
  |- log/
  |- public/
  |- test/
  |- vendor/
  |  |- assets/
  |  |  |- bower_components/
  |  |  |  |- third libararies/
  |- |  |- bower.json
  |- Bowerfile # bower package dependencies
  |- config.ru
  |- gulpfile.js
  |- package.json
  |- config.ru
  |- Gemfile
  |- Gemfile.lock
  |- Guardfile # Guard file for livereload
  |- Rakefile
  |- README.rdoc
```

## Running example
![alt text](https://raw.githubusercontent.com/hung-phan/generator-rails-react-webpack/master/screenshot.png "application screenshot")

## Contribution
All contributions are welcomed.

## License

[MIT License](http://en.wikipedia.org/wiki/MIT_License)
