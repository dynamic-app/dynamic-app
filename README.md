
# DynamicApp
Application Flow Manager tools. 

## Introduction
Registers ***services*** and ***components***,
and manages flexible ***containers*** by objects of definitions.

See example **[dynamic-app-boilerplate](https://github.com/dynamic-app/dynamic-app-boilerplate)**. 

## The innovations
- Ability to inherit and reuse containers
- Independence of routing to layout hierarchy
- Display components and layout according to device type
- Include components independent of one framework

## Let's see what it looks like
the code:
```js

const services = {
  myService_1,
  myService_2
}

const widgets = {
  myComponent_1,
  myComponent_2
}

const containers = { 
  home: {
    route: '/',
    services: {}, // using the services list
    widgets: {} // using the widgets list
  }
}

DynamicApp.setConfig({
  services,
  widgets,
  containers
});

DynamicApp.flash(); // run the app
```

## The functions
```js
// Configs
DynamicApp.setConfig(configs)
DynamicApp.flash()

// Navigator
DynamicApp.goTo(path)
DynamicApp.goBack()

// States
DynamicApp.activeState(states, flash = true)
DynamicApp.unactiveState(states, flash = true)
DynamicApp.getActiveStates(filter)
```

## API

```js
DynamicApp.setConfig({
  
  services: {
    [service_id]: function() {} || Class,
  },

  widgets: {
    [widget_id]: function(el) {} || `template strings`,
  }, 
  
  containers: {
    [container_id]: {
      extends: '[container_id]',
      route: '[window.location(url-pattern)]',
      state: '[hidden-location(url-pattern)]', // using localStorage
      
      services: {
        [item_id]: {
          serviceId: '[service_id]',
        },
      },
     
      widgets: {
        [item_id]: {
          widgetId: '[widget_id]',
          [includeIn||includeBefore||includeAfter]: '[css selectors]',
        },
      },
    },
  }
}
```

# license
MIT







