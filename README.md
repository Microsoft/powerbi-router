# powerbi-router
[![Build Status](https://travis-ci.com/Microsoft/powerbi-router.svg?token=nXyWFYxRu6tVxUMJAuJr&branch=master)](https://travis-ci.com/Microsoft/powerbi-router)

Router for Microsoft Power BI. Given an http method and url pattern call the matching handler with the request and response object. Syntax matches common libraries such as express and restify.
This library uses [Route-recognizer](https://github.com/tildeio/route-recognizer) to handle pattern matching such as `/root/path/:name` where `name` will be passed as paramter to the handler.

## Installation:
```
npm install --save powerbi-router
```

## Usage:
```
import * as Wpmp from 'window-post-message-proxy';
import * as Router from 'powerbi-router';

const wpmp = new Wpmp.WindowPostMessageProxy();
const router = new Router.Router(wpmp);

router.get('/report/pages', (request, response) => {
  return app.getPages()
    .then(pages => {
      response.send(200, pages);
    });
});

router.put('/report/pages/active', (request, response) => {
  app.setPage(request.body)
    .then(page => {
      host.sendEvent('pageChanged', page);
    });
    
  response.send(202);
});
```

