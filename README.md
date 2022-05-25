# Lets.js
It’s just an idea of natural language that binds to Node.js API

## Example 

Following code in **Lets**:

```bash
Let's start http server on localhost with port 8082.
```

would generate code(using cutie-http library):

```

'use strict'

const {
  Event
} = require('@cuties/cutie');
const {
  CreatedHttpServer,
  ListeningServer,
  EndedResponse
} = require('@cuties/http');

class RequestResponseEvent extends Event {

  constructor() {
    super();
  }

  body(request, response) {
    // handle request
    new EndedResponse(response, 'response').call();
  }

}

new ListeningServer(
  new CreatedHttpServer(
   new RequestResponseEvent()
  ), 8082, '127.0.0.1'
).call()

```
