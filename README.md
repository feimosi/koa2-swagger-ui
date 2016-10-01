# koa2-swagger-ui

[![NPM version][npm-image]][npm-url]
[![build status][travis-img]][travis-url]
[![Dependency Status][david-img]][david-url]

[npm-image]: https://img.shields.io/npm/v/koa2-swagger-ui.svg
[npm-url]: https://npmjs.org/package/koa2-swagger-ui
[travis-img]: https://travis-ci.org/scttcper/koa2-swagger-ui.svg
[travis-url]: https://travis-ci.org/scttcper/koa2-swagger-ui
[david-img]: https://img.shields.io/david/scttcper/koa2-swagger-ui.svg
[david-url]: https://david-dm.org/scttcper/koa2-swagger-ui

Host swagger ui at a given directory from your koa v2 app.

Inspired by:
- [swagger-injector](https://github.com/johnhof/swagger-injector) for serving on a specific route
- [hapi-swaggered-ui](https://github.com/z0mt3c/hapi-swaggered-ui) for serving files from node_modules using a handlebars driven index.html

## install
```
npm install koa2-swagger-ui --save
```

## config
for more swaggerOptions see [swagger-ui](https://github.com/swagger-api/swagger-ui#swaggerui)
defaults:
```javascript
title: 'swagger', // page title
oauthOptions: {}, // passed to initOAuth
swaggerOptions: { // passed to SwaggerUi()
  dom_id: 'swagger-ui-container',
  url: 'http://petstore.swagger.io/v2/swagger.json', // link to swagger.json
  supportedSubmitMethods: ['get', 'post', 'put', 'delete', 'patch'],
  docExpansion: 'none',
  jsonEditor: false,
  defaultModelRendering: 'schema',
  showRequestHeaders: false,
},
routePrefix: '/docs', // route where the view is returned
```

## example
```javascript
const Koa = require('koa');
const koaSwagger = require('koa2-swagger-ui');

const app = new Koa();


app.use(koaSwagger({
  routePrefix: '/swagger', // host at /swagger instead of default /docs
  swaggerOptions: {
    url: 'http://petstore.swagger.io/v2/swagger.json', // example path to json
  },
}));

app.listen(3000);
```
