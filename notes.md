# Start Learning React
- Joe Maddalone
- Started 11-05-2017

## Use create-react-app to Setup a Simple React App
- Install the package with `npm i create-react-app -g`
- Set up a new project with `create-react-app react-app`
- Start the script with `npm start`
- Delete all the files except 
    - scr/App.js, rewrite with:
    ```js
    import React from 'react';

    const App = () => <h1>Hello</h1>

    export default App
    ```
    - src/index.js, rewrite with:
    ```js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import App from './App';

    ReactDOM.render(
    <App />, 
    document.getElementById('root')
    );
    ```
    - rewrite public/index.html with
    ```js
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="utf-8">
        <title>React App</title>
    </head>
    <body>
        <div id="root"></div>
    </body>
    </html>
    ```

## Write a "Hello World" React Component
- We create a class
- We use className since class is a reserve keyword
- We use JSX in React
```js
// App.js
class App extends React.Component {
  render() {
    return <h1 className="">Hello World</h1>
  }
}
```

- React compiles to JS:
```js
// App.js
class App extends React.Component {
  render() {
    return React.createElement('h1', null, 'Hello Eggheads')
  }
}
```

- Now we create a stateless function
```js
// App.js
const App = () => <h1>Hello stateless</h1>
```

## Display Output in React with a Component's render Method
- We can return a single node in class
- This doesn't work:
```js
// App.js
class App extends React.Component {
  render() {
    return <h1>Hello World</h1> <b>Bold</b>
  }
}
```

- You need to create a parent wrapper like a div
```js
// App.js
class App extends React.Component {
  render() {
    return ( 
        <div>
            <h1>Hello World</h1>
            <b>Bold</b>
        </div>
    )
  }
}
```

## Set Properties on React Components
- We can set props to be accessed
```js
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
<App text="this is the prop text" />, 
document.getElementById('root')
);

// App.js
class App extends React.Component {
    render() {
        return <h1>{this.props.text}</h1>
    }
}
```

- We can also set prop types:
```js
// index.js
ReactDOM.render(
    <App cat={5} text="this is the prop text" />,
    document.getElementById('root')
)
// App.js
App.propTypes = {
    txt: React.Proptypes.string,
    cat: React.Proptypes.number.isRequired
}
```

- Can also set default props:
```js
App.defaultProps = {
    text: "this is the default text"
}
```

## Manage React Component State with setState
- We can also apply different states to our components
```js
class App extends React.Component {
    constructor() {
        super();
        this.state = {
            txt: 'this is the state txt'
            cat: 0
        }
    }

    update( e ) {
        this.setState({txt: e.target.value})
    }

    render() {
        return (
            <div>
                <input type="text"
                    onChange={this.update.bind(this)} />
                <h1>{this.state.txt} - {this.state.cat}</h1>            
            </div>
        )
    }
}
```