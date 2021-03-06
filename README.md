# JSON Server [![Build Status](https://travis-ci.org/typicode/json-server.svg)](https://travis-ci.org/typicode/json-server) [![NPM version](https://badge.fury.io/js/json-server.svg)](http://badge.fury.io/js/json-server)

> Get a full fake REST API with __zero coding__ in __less than 30 seconds__ (seriously)

Created with <3 for front-end developers who need a quick back-end for prototyping and mocking.

Powers [JSONPlaceholder](http://jsonplaceholder.typicode.com)

## Example

Create a `db.json` file

```javascript
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ]
}
```

Start JSON Server

```bash
$ json-server db.json
```

Now if you go to [http://localhost:3000/posts/1](), you will get:

```javascript
{ 
  "id": 1,
  "body": "foo"
}
```

Also, data is persisted to `db.json` when you make POST, PUT, PATCH and DELETE requests. So it's a fully functional fake REST server.

## Routes

In fact, you instantly get all these routes:

```
GET   /posts
GET   /posts?title=json-server&author=typicode
GET   /posts/1/comments
GET   /posts/1
POST  /posts
PUT   /posts/1
PATCH /posts/1
DEL   /posts/1
```

To slice resources, add `_start` and `_end`.

```
GET /posts?_start=0&_end=10
GET /posts/1/comments?_start=0&_end=10
```

To sort resources, add `_sort` and `_order` (ascending order by default).

```
GET /posts?_sort=views&_order=DESC
GET /posts/1/comments?_sort=votes&_order=ASC
```

To make a full-text search on resources, add `q`.

```
GET /posts?q=internet
```

Returns database.

```
GET /db
```

Returns default index file or serves `./public` directory.

```
GET /
```

## Install

```bash
$ npm install -g json-server
```

## Extras

### Static file server

You can use JSON Server to serve your HTML, JS and CSS, simply create a `./public` directory.

### Access from anywhere

You can access your fake API from anywhere using CORS and JSONP.

### Remote schema

You can load remote schemas:

```bash
$ json-server http://example.com/file.json
$ json-server http://jsonplaceholder.typicode.com/db
```

### JS file support

You can use JS to programmatically create data:

```javascript
module.exports = function() {
  data = { users: [] }
  // Create 1000 users
  for (var i = 0; i < 1000; i++) {
    data.users.push({ name: 'user' + i })
  }
  return data
}
```

```bash
$ json-server index.js
```

### Module

You can use JSON Server as a module:

```javascript
var server = require('json-server')

server({
  posts: [
    { id: 1, body: 'foo' }
  ]
}).listen(3000)
```

### Deployment

You can deploy JSON Server. For example, [JSONPlaceholder](http://jsonplaceholder.typicode.com) is an online fake API powered by JSON Server and running on Heroku.

## Links

### Articles

* [Fast prototyping using Restangular and Json-server](http://bahmutov.calepin.co/fast-prototyping-using-restangular-and-json-server.html)
* [ng-admin: Add an AngularJS admin GUI to any RESTful API](http://marmelab.com/blog/2014/09/15/easy-backend-for-your-restful-api.html)

### Projects

* [Grunt JSON Server](https://github.com/tfiwm/grunt-json-server)
* [docker-json-server](https://github.com/clue/docker-json-server)
* [JSON Server GUI](https://github.com/naholyr/json-server-gui)

## License

MIT - [Typicode](https://github.com/typicode)
