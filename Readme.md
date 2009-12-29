
# Express
      
  Insanely fast (and small) server-side JavaScript web development framework
  built on **node.js** and the **V8 JavaScript engine**.

  * Visit the [Wiki](http://wiki.github.com/visionmedia/express) for documentation
  * Visit the [Google Group](http://groups.google.com/group/express-js) for discussion

## Features (so far)

  * Sexy DSL with robust sinatra-like routing
  * High performance
  * Mime helpers
  * Redirection helpers
  * Nested parameter parsing
  * Full test coverage
  * Extremely readable specs
  * Test helpers (mock requests etc)
  * Environment based configuration
  * Light-weight JavaScript class implementation via js-oo
  * Collections and chainable iterators
  * ElementCollections / markup parsing via libxmljs and css selector traversal support via css2xpath
  * View support (ejs, haml, mustache)
  
## Installation

Currently Express must be cloned (or downloaded), you can use the following command to
get rolling and initialize the submodule dependencies:

    $ git clone git://github.com/visionmedia/express.git && cd express && git submodule update --init && make app
    
Or with the [gh](http://github.com/visionmedia/gh) utility:

    $ gh clone visionmedia express && cd express && git submodule update --init && make app

## Performance

  Extensive benchmarking will wait until a development version
  has been released. 
  
  Currently Express can chew through a request with a two Haml views (*page and layout*) 
  requested **2000** times with concurrency of **80** in **2.4** seconds and **814**
  requests per second. With no caching involved.
  
  An identical Sinatra application was served with the **Thin** HTTP server
  and scored **8.3** seconds and **238** requests per second. In this situation
  Express is currently **3.5** times faster than Sinatra.

## Examples

    require.paths.unshift('lib')
    require('express')
    require('express/plugins')
    
    configure(function(){
      use(MethodOverride)
      use(ContentLength)
      use(Redirect)
      set('root', dirname(__filename))
      enable('cache views')
    })
    
    get('/hello', function(){
      this.contentType('html')
      return '<h1>World<h1>'
    })
    
    get('/user/:id?', function(id) {
      this.render('user.haml.html', {
        locals: {
          name: id ? 'User ' + id : 'You' 
        }
      })
    })
    
    run()
  
## Running Tests

Express uses the [JSpec](http://jspec.info) BDD JavaScript testing
framework to write and run elegant spec suites. JSpec is froozen 
to spec/lib and does not require seperate installation.

To run all specifications:

    $ make test
    
Run individual suites:

    $ node spec/spec.node.js core
    $ node spec/spec.node.js mime
    $ node spec/spec.node.js routing
    ...

Express is currently being developed with node --version:
    v0.1.21-66-g59a78d6
    
## Contributors

* TJ Holowaychuk (visionmedia) &lt;tj@vision-media.ca&gt;
* Ciaran Jessup (ciaranj) &lt;ciaranj@gmail.com&gt;
    
## License 

(The MIT License)

Copyright (c) 2009 TJ Holowaychuk &lt;tj@vision-media.ca&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
