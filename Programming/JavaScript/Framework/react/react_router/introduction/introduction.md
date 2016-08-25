## Introduction [Back](./../react_router.md)

Think about a case that without refreshing, how can we keep the URL in sync with contents in a page?

React Router is used to help adding new screens and flows to our application, while keeping the URL in sync with what's being displayed on the page.

### Without React Router

If we don't use React Router, we are supposed to complete this requirement with `window.location.hash`.

```js
import React from 'react';
import { render } from 'react-dom';

const About = React.createClass({/*...*/});
const Inbox = React.createClass({/*...*/});
const Home = React.createClass({/*...*/});

export class App extends React.Component {
    constructor(props) {
        super(props);
        
        this.state = { route: window.location.hash.substr(1) };
    }
    
    componentDidMount() {
        window.addEventListener('hashchange', () => {
            this.setState({
                route: window.location.hash.substr(1)
            });
        });
    }
}
```