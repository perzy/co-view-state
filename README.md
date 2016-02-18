# co-view-state

View state middleware for Koa.

## Installation

```js
$ npm install co-view-state
```

```js
var viewState = require('co-view-state');

var koa = require('koa');
var render = require('koa-swig');
var app = koa();

// extends view locals
app.use(viewState());
// render
app.context.render = render({
  root: path.join(root, 'app/views'),
  autoescape: true,
  // disable, set to false or 'memory'
  cache: 'production' === app.env ? 'memory' : false,
  ext: 'html',
  locals: locals,
  writeBody: true,
  //filters: filters,
  //tags: tags,
  //extensions: extensions
});

app.use(function* (){
  var options = { name: 'jerry wu' };
  yield this.render('home', options);
});

app.listen(3000);
console.log('listening on port 3000');
```

## View html
 
 app/views/home.html
 
```
<div>name: {{name}} </div>

user:

<div>
   nickname: {{user.nickname}}
   age: {{user.age}}
   ...
</div>
  
```

## License

  MIT