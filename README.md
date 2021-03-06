aja.js
======

Ajax without XML : Asynchronous Javascript and JavaScript/JSON(P)

## Basic Sample

Request JSON data

```javascript
  aja()
    .url('/api/data.json')
    .on('success', function(data){
        //data is a JavaScript object
    })
    .go();
```

Load html into an element

```javascript
  aja()
    .url('/views/page.html')
    .into('.container')
    .go();
```

More options using the fluent api, terrific REST client.

```javascript
  aja()
    .method('GET')
    .url('/api/customer')
    .data({firstname: 'John Romuald'})
    .on('200', function(response){
        //well done
    })
    .go();

  aja()
    .method('PUT')
    .url('/api/customer')
    .cache(false)
    .body({id : 12, firstname: 'John Romuald', job : 'linguist'})
    .on('200', function(response){
        //well done
    })
     .on('40*', function(response){
        //something is definitely wrong
    })
    .on('500', function(response){
        //oh crap
    })
    .go();
```

JSONP

```javascript
  aja()
    .url('http://otherdomain.com/api/remoteScript')
    .type('jsonp')
    .padding('someGlobalFunction')
    .on('success', function(data){
        //Fuk cross origin policy
    })
    .go();
```

## Development

### Setup

You need [grunt >= 0.4][grunt] as well as [node] and [npm] installed and running on your system.

```
git clone https://github.com/krampstudio/aja.js.git
cd aja.js
npm install
```

### Tests

Run the tests:

```
grunt test
```

### Development

The dev of this library is based on TDD principle. So, dev means *write tests*. Run the developent server :

```
grunt devtest
```

So tests run once something is modified and you can access it also at http://localhost:9901/test

## Contributing

Contributions (issue reporting, bug fixes, feedback, typos, gimie a tip, etc.) are really welcomed!
This library is developed using the TDD principles, so I accept pull request only if they come with the according unit/integration test.

> I'd love if somebody can create a nice logo for aja.js...

## History

 - _0.1.0_ : initial release
 - _0.2.0_ : added support of new HTTP methods (trace, patch and connect)
   - _0.2.1_ : Fix missing  `main` prop in package.json
 - _0.3.0_ : support new request type : script
   - _0.3.1_ : Fix issue #4 and cache management

## License

Copyright (c) 2014 Bertrand Chevrier `<"chevrier_bertrand gmail_com".replace(/\s/, '@').replace(/_/g, '.')>`
Licensed under the MIT license.


[grunt]: https://gruntjs.com
[node]: http://nodejs.org
[npm]: http://npmjs.org
