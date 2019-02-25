# react

## LifeCycle

Every component follow a cycle from when it is created and mounted to DOM to when it is unmounted and destroyed, This is refer to as the component lifecyle.
we get several lifecyle methods in this process. they are embeded in the react library, they get called automatically at the each point of lifecyle, which can effectively control and manipulate what goes on in a component throughout its lifetime.

#### mount 
- react use React.createElement(component,props);
1. initializatio and construction 
    - set default props and state,defaultProps(es6) createClass=>getDefaultProps(Es5)
2. pre-mounting
    - componentWillMount is called and is only called one time and before the initial render. It is a chance for us to handle configuration and update the state and in general prepare for the first render.
3. component render()
    - render function should be a pure fucntion, it should not use setState and access DOM node
4. managing children components and mounting 
5. post-mounting
    - componentDidUpdate works from the bottom up 
    - interact with the Native UI and third party UI library.(v3,date range picker)
    - start AJAX call to load data for the component

#### update
- change of props, change of state and calling forceUpdate will trigger rerender.

1. componentWillRecieveProps: it can access two value, next value and current value(this.props.). it acts on particular change on props to trigger state transtion
2. componentShouldUpdate: it prevent unneccessary render,it shollow compare next props and state, if they are different, function will return true, the component will render, if return false, it will 
3. componentWillUpdate: nextPros and nextState. It just like the componentWillMount, can manipulate the data before render, It gets called everytime the component need update, so do not setstate in this lifecycle, it will cause infinite loop.
4. componentDidUpdate: update DOM in response to props or state change 
5. forceupdate()

#### unmount

1. componentWillUnmount: it do some cleanupthings, such as invalidating timers, canceling network requests, removing event listeners or canceling any subscriptions made in componentDidMount.
----

## state and props
- state is an object that hold some information that may change over the lifetime of the component, it is a an internal object that is not defined by outside value. we prefer to lift state up in the practise. 
- props is input to the component,they pass data down from a parent to a child component.
- difference: not every component contains a state, props get passed to components similar to function paramenter whereas state is managed within the component similar to variable declared in the function.




Let's take a quick moment and discuss the process of application architecture. We often hear about over-architected systems. This often occurs when we try to plan for every possible scenario that could ever occur through the life of an application. To try and support every conceivable use is a fools errand. When we try to build these systems we add unnecessary complexity and often make development harder, rather then easier.
At the same time, we don't want to build a system that offers no flexibility at all. It may be faster to just build it without future thought, but adding new features can be just as time consuming later on. Trying to find the right balance is the hardest part of application architecture. We want to create a flexible application that allows growth but we don't want to waste time on all possibilities.
The other challenge with application architecture is trying to understand our needs. With development, we often have to build out something to truly understand it. This means that our application architecture is a living process. It changes over time due to having a better understanding of what's required. Refactoring Components is critical to the success of a project and makes adding new features easier.

Because of this process, we felt it is important to walk through the evolution of a Component. We will start with a naive approach to building a List Component and then walk through different refactorings to support reusability. More then likely, we would know early on that a List should be reusable. But, walking through the evolution process can help deepen our understanding of how to enable reusability.

## pureComponent
- PureComponent is exactly the same as Component except that it handles the shouldComponentUpdate method for you. When props or state changes, PureComponent will do a shallow comparison on both props and state. Component on the other hand won’t compare current props and state to next out of the box. Thus, the component will re-render by default whenever shouldComponentUpdate is called.

## stateless Component
- Stateless Components are easy and fast to implement. They don't have state and life cycle method. They are good for very small UI view where re-render cost won’t matter that much. They provide cleaner code and less number of files to deal with.

## redux

1. what is redux?
redux is a state management tool, it follow the flux design pattern which only allow unidirectional data flow. it helps to manage states shared across components.
2. work flow for the redux 
There are several important parts in redux, such as action reducer and store, we need use connect to attach target component to the redux, connect can pass two argument, one is mapstateToProps, another is mapDispatchToProps. when something required to change, component will invoke a action creator to dispatch a action and then reducer recieve the action, depend on it action type and payload, it could manipulate the center store, and then component can fetch the correct state value. 
3. handle asynchronous call in redux 
I used to use redux-thunk to handle asynchronous call in redux, in the actionCreator function, instead of return a action, we can return a function within there are many dispatches. we need break an asynchronous action into at least three synchronous actions, They are started, was succeessfully completed, failed.
4. redux middleware 
Middleware provides a way to interact with actions that have been dispatched to the store before they reach the store's reducer. Examples of different uses for middleware include logging actions, reporting errors, making asynchronous requests, and dispatching new actions.

    ```javascript
    const logAction = store => {
        return next => {
            return action => {
                const result = next(action);
                console.log(
                `caught in the middleware ${JSON.stringify(store.getState())}`
                );
                return result;
            };
        };
    };
    const store = createStore(reducer, applyMiddleware(logAction));
    ```
