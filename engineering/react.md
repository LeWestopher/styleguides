# React.js Style Guide

## Table Of Contents

* [Naming Conventions](#naming)
* [Minimizing Stateful Components](#general)
* [Component Interface Composition](#organizing-your-modules)
* [Properly Binding Class Components](#models)
* [Component Best Practices](#controllers)
* [Using Index as Key Props](#templates)


## Naming Conventions

### In React, if you are rendering your component using JSX, the name of that component has to begin with a capital letter.

There are caveats to how the component can be defined versus imported and still allow successful rendering, but for sake of best practices you should just always resort to defining your JSX rendered components with a capital letter.

```html
// Good
<MyComponent>
    <App /> // Will work!
</MyComponent>

// Bad
<MyComponent>
    <app /> // Will not work :(
</MyComponent>
```

### Boolean variables, or functions that return a boolean value, should start with “is,” “has” or “should.”

Boolean variables should be well defined and verb based to enhance their comprehension between developers.

```javascript
// Good
const isComplete = current >= goal;

// Bad
const done = current >= goal;
```

### Functions should be named for what they do, not how they do it.

Don’t expose details of the implementation in the name. Why? Because how you do it may change some day, and you shouldn’t need to refactor your consuming code because of it. 

```javascript
// Good
const loadConfig = () => {
  ...
};

// Bad
const loadConfigFromServer = () => {
  ...
};
```

## Minimizing Stateful Components

TBD


```js

```


## Component Interface Composition

### Organization

Text Text Text

```js
// Good

// Bad

```

## Properly Binding Class Components

### Binding via arrow function

Text Text Text

## Component Best Practices

### Utilize pure functional components as much as possible

With the latest versions of React, there is little reason to opt for class based components anymore.  The addition of methods such as `useState()` and `useEffect()` allow us to tap into the state management and component lifecycle functionalities previously only available on class components.  Previous behavior implemented in `componentDidUpdate()`, `componentDidMount()`, and `shouldComponentUpdate()` can be implemented using `useEffect()`.

```JSX
// Bad
import React, { Component } from 'react'
import { fetchTime } from './api'

class Clock extends Component {
  render () {
    const { currentTime } = this.state
    return (<div>
      <div>
        Current Time: {currentTime}
      </div>
    </div>)
  }

  componentDidMount() {
    fetchTime()
      .then(currentTime => { this.setState({ currentTime })})
  }
}
```

Instead you can use a functional component using `useState()` and `useEffect()`:

```JSX
// Good
import React, { useEffect } from 'react'
import { fetchTime } from './api'

const Clock = () => {
  const [currentTime, setCurrentTime] = useState()
  
  useEffect(() => {
    // Will run once the component is mounted
    fetchTime()
      .then(currentTime => setCurrentTime(currentTime))
  })

  return (
    <div>
      <div>
        Current Time: {currentTime}
      </div>
    </div>
  )
}

export default Clock;
```



### Use default argument values to create default values for components

Text Text Text

```javascript

```

### Separate stateful aspects from rendering

Having state functionality mixed with rendering makes for harder code to test.  For example, we would not be able to test the rendering functionality of the following User component in isolation due to the 

```javascript
// Bad
import React, { useState, useEffect } from 'react'
import { fetchUser } from './api';

const User = ({ id }) => {

  const [isLoading, setIsLoading] = useState(true)
  const [user, setUser] = useState()

  useEffect(() => {
    return fetchUser(id)
      .then((user) => {
        setIsLoading(false)
        setUser(user)
      })
  })

  return loading
      ? (<div>Loading...</div>)
      : (<div>
          <div>
            First name: {user.firstName}
          </div>
          <div>
            First name: {user.lastName}
          </div>
          ...
        </div>);
}
```
To avoid this, we can utilize a decorator pattern via React's higher order components pattern.  In this example, we seperate the rendering logic into a dynamically rendered component that accepts a `user` prop.  Now the rendering logic can be tested cleanly in isolation without worrying about the accessing the state or HTTP services.
```JSX

// Good
import React, { useState, useEffect } from 'react'
import { fetchUser } from './api';
import RenderUser from './RenderUser';
import Loading from './Loading';

const withFetchUser = (RenderUserComponent) => ({ id }) => {

  const [isLoading, setIsLoading] = useState(true)
  const [user, setUser] = useState()

  useEffect(() => {
    return fetchUser(id)
      .then((user) => {
        setIsLoading(false)
        setUser(user)
      })
  })

  return loading
      ? (<Loading />)
      : (<RenderUserComponent user={user} />);
}

// Usage
const UserComponent = withFetchUser(RenderableUserComponent)
```

### Optimize render efficiency by skipping non-needed updates

An array can be passed into the second argument of `useEffect()` that will determine the conditions upon which the effect should run again.  This is a simple comparison array that will determine whether or not the effect should be run again.  For example, let's say we pass in an array with a single element: the User ID of the current user we are trying to render for - the effect would only run again once the ID in that array changed.

```JSX
// In our withFetchUser HOC:

const id = props.id
const [isLoading, setIsLoading] = useState(true)
const [user, setUser] = useState()

useEffect(() => {
  return fetchUser(id)
    .then((user) => {
      setIsLoading(false)
      setUser(user)
    })
}, [id])

```

## Using Index as Key Props

Text Text Text
```js
// good

// bad

```