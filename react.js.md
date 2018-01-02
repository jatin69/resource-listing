# React.js

## Nice watches
- [Flux workflow talk ](https://www.youtube.com/watch?v=xsSnOQynTHs)
- [Declarative Programming](https://youtu.be/yGh0bjzj4IQ)

# Resources
- [Awesome React guide github](https://github.com/enaqx/awesome-react#react-and-socketio)
- [Online editor](https://codesandbox.io/)


## Why is it called scalable ?
Once we get familiar with react life cycle, we can clearly observe that,
each component is an independent entity encapsulated in higher entities.
It has all its classes as well as behaviour.

# Thinking Different

### Classic approach
- generate html on server side, send to browser.
- **The content comes from source A, then combined with a template residing in source B,
html generated and then sent to browser.**
- if i need more news feed, re generate it all and send to browser.
- fresh html loaded as a whole, old ones either get lost, or
if explicitly maintained increase page size that needs to be sent from server.
- In modern cases, AJAX used if you wanna prevent page reload. But it's just a third party code managing the scaling.
The foundation isn't built to scale.

### React approach
- each component is complete as a whole.
- Initially a few feeds are sent to browser as html.
- Now if i need more events, new posts are fetched from the api,
components updated in the virtual DOM, diff calculated, and the minimal updation in real dom is performed.
- In this way, unlimited number of smaller components can be fetched from server.
- The browser page isn't reloaded, so all the old posts remain there.
- when those are further interacted with, requests are sent to server, virtual DOM updation occurs,
components further rendered in Real DOM. **all of it without reloading the page.**
- writing all html inside javascript. hello JSX


## Learnings

- If you need to apply if else logic to return jsx as per the data, break it into smaller functions.
Always call functions. It'll keep the code plain and simple.
- Create a class only when you need to associate a state with it. Keep only those functions inside,
which change state or are directly affecting state. For all other functionalities, functions will do fine.
- Props never mutate. Follow this advice.
- If a change is required, make separate functions, call them by if else logic.

- In React, you can create distinct components that encapsulate behavior you need.
Then, you can render only some of them, depending on the state of your application.

- Be super careful with events. onClick() when used as onClick, needs to be bound. or use class field syntax () => { }

- Also these need to be passed on to the core elements to provide the functionalities. for eg, a ButtonControl class
will have to pass on onClick functionality to individual button.

- There should be a single **“source of truth”** for any data that changes in a React application. Usually, the state is first added to the component that needs it for rendering. Then, if other components also need it, you can lift it up to their closest common ancestor. Instead of trying to sync the state between different components, you should rely on the top-down data flow.

- Composition over Inheritance
	- a subcomponent reads input
	- passes data to a common parent (common parent of members whose state depend on this input)
	- This parent then becomes the single source of truth, and distributes this data in top down manner, to all component who need it.
	- The components then respond to this calling and all setState to change and re renders itself.
	- what happens is -> components are given an illusion that they are in control of the state change, whereas the actual change occurs in parent.

- we always say that a component should manage the state by itself. But, when two components are in sync,
we find a common parent, or create one if it doesn't exist, and follow the above approach.

- **State Lifting** 
	- When you want to aggregate data from multiple children or to have two child components communicate with each other, move the state upwards so that it lives in the parent component. 
	- The parent can then pass the state back down to the children via props, so that the child components are always in sync with each other and with the parent.

- **Declarative**, **Idempotent Actions** and **Uni Direction Data flow**
Because buttons only call handlers and do not directly change anything,
the actions are idempotent. It will not matter if i pressed the button multiple times, because what will happen due to that click is idempotent. So assuming, i click the PAYMENT button, handler is still processing my transaction,
then if i further press the button 2 times, it will not cause the repetition of payment. 
WHY ? Because that very specific click handler knows that a current transaction is in process, thus it will not act
any further on that request.