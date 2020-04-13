# Unit Test
To be aplied in unity most small of a software (component). Are to confirm about they works good.

# Integration Test
Are a extension of unit test, later you test each part of functionality. You can test how to work integrating it.

# Functional Test
Usually maded by testing teams, called 'black box' because testing team analize input data and output data to define test cases.

# Performance Test
Are for test quality, escalability and security of system


## Jest
Any program feature without an automated test simply doesn't exist.
Test Runer. Is a freamework to test, maded in javascript. Can be used in:
- Babel
- React
- Typescript
- NodeJs
- Angular
- Vue
Was maded by facebook dev team like React. Are used by fb, ig, tw, airbnb, NyTimes, Spotify, etc..

#### Why Jest?
- Fast and safe
When you run test and one fail, in the next execution this will run first the fail test.
- Easy mocking
- Great exceptions (output on errors)
- Great api (documentation)

## Enzyme
Is a utility of testing in javascript (specially for react) was created to easily test in react components. Was maded by Airbnb. With Enzyme can manipule find and interact with elements of each component (div, p, img, any) like jquery (not the same).
Alternative for mocha

## Common Folder Structures
````
|- / main
|  |- index.js
|  |- index.test.js
```

````
|- / main
|  |- index.js
|- / supporting
|  |- fetch.js
|- / tests
|  |- /int
|  |  |- api.test.js
```

````
|- / main
|  |- index.js
|- / supporting
|  |- fetch.js
|- / __tests__
|  |- /components
|  |  |- index.test.js
```

## Example
```javascript
import React from 'react'
import Enzyme, {shallow} from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'

enzyme.configure({adapter: new Adapter()})

import CheckboxWithLabel from '../CheckboxWithLabel'

it('CheckboxWithLabel changes the text after click', () => {
  const checkbox = shallow(<CheckboxWithLabel labelOn="On" labelOff="Off" />)
  expect(checkbox.text()).toEqual('Off')
  checkbox.find('input').simulate('change')
  expect(checkbox.text()).toEqual('On')
})
```

# Enzyme
## Selectors
### Valid CSS
Get components by Tag name, Class, ID, syntax like ([href="foo"], [type="text"]), or universal (*)

### Constructor
Find componeny by constructor
```javascript
function MyTestComponent() {
  return <div/>
}
const myComponents = wrapper.find(MyTestComponent) // find all results with this constructor
```

### displayName
Find by displayName property
```javascript
function MyTestComponent() {
  return <div/>
}
MyTestComponent.displayName= 'Testing';
const myComponents = wrapper.find('Testing') // find one component with displayName Testing
```

### Props
Find by props
```javascript
const wrapper = mount()((
  <div>
    <span title="foo" description="Lorem ipsum" />
  </div>
))
wrapper.find({ title: 'foo'}) // return component
wrapper.find({ description: 'Lorem ipsum'}) // return component
wrapper.find({ title: 'bar'}) // return undefined
```

## Shallow Rendering
Is one of the techniques to use and inspect components, and lifeCycle methods of this.
Find one component contains others components inside, or find elements.
shallow() spect a node(component) and extra optionals like (context and disableLifecycleMethods)

## Globals
default is a var, per default is 5 segs
### beforeAll (fn, timeout)
### beforeEach (fn, timeout)
### describe (name, fn)
### test or it (name, fn, timeout)

## Mock Functions
```javascript
function forEach(items, callback) {
  for (let index = 0; index < items.length; index++) {
    callback(items[index])
  }
}
const mockCallback = jest.fn(x => 42 + x)
forEach([0, 1], mockCallback)

// The mock function is called twice
expect(mockCallback.mock.calls.length).toBe(2)

// The first argument of the first call to the function was 0
expect(mockCallback.mock.calls[0][0]).toBe(0)

// The first argument of the second call to the function was 1
expect(mockCallback.mock.calls[1][0]).toBe(1)

// The first argument of the first call to the function was 42
expect(mockCallback.mock.calls[0].value).toBe(42)
```

```javascript
// users.test.js
import axtios from 'axios'
import Users from './users'

jest.mock('axios')

test('should fetch users', () => {
  const users = [{name: 'Bob'}]
  const resp = {data: users}

  axios.get.mockResolvedValue(resp)
  // or you could use the following depending on your use case:
  // axios.get.mockImplementation(() => Promise.resolve(resp))
  return Users.all().then(data => expect(data).toEqual(users))
})
```

## Assertions
### Expect
- expect(value)

#### Matchers:
- .toBe(value)
- .toHaveBeenCalled()
- .toHaveBeenCalledTimes(number)
- .toBeDefined()
- .toBeFalsy()
- .toBeGreaterThan(number)
- .toBeNull()
- .toBeTruthy()
- .toBeUndefined()
- .toBeNaN()
- .toEqual(value)
- .toHaveLength(number)
- .toThrow(error?)
- more in documentation


################### END ###################
- `npx create-react-app unit-test-react`
- `npm i axios react-redux react-router-dom redux redux-saga prop-types`
Not need install jest, because CRA install this.
- `npm install --save enzyme enzyme-adapter-react-16`
- Create setupTests with enzyme config to set adapter to enzyme config.
- `--env=jsdom` is for mock browser in test environment
- `npm i @material-ui/core` create config/muiTheme.js and use provider in app.js
- `npm i react-jss` create config/jssConfig.js, add `<!-- jss-insertion-point -->` in index.html and use provider in app.js


################### END ###################

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `yarn build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
