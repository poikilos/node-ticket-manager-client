# node-ticket-manager-client
This is the client (worker) part of
<https://github.com/poikilos/node-ticket-manager>.

## Install

```
cd node-ticket-manager-client
yarn
```

## NodeJS Module Usage
Create a lib/config/config.js similar to the config.default.js file
there, but do not use the default passwords! Match them to the settings
in node-ticket-manager.


```javascript
var  TicketWorker = require("node-ticket-manager").TicketWorker;
var  TicketManager = require("node-ticket-manager").TicketManager;
```

## TicketManager API

```
new TicketManager : (@name, @host, basicAuth) ->

TicketManager.issue()
// issue : (title, category, content, callback)->
```

## TicketWorker API

### Instance construction
```
  constructor: (options={}) ->
  # @param {Object} options, optionally includes:
  #     options.name
  #     options.id
  #     options.consumerSecret
  #     options.host
  #     options.category
  #     options.timeout : ticket processing timeout in ms
  #     options.interval : self checking interval
  #     options.basicAuth : basicAuth
  #
```

### Events:
- on "new ticket", listener signature: `eventListener(ticket)`
- on "complete", listener signature: `eventListener(ticket)`
- on "giveup", listener signature: `eventListener(ticket)`

### Instance Methods
- complete : `()->`
- update : `(message, kind='default')->`
- giveup: `(reason)->`


