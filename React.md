# <mark>DOM</mark>

## What is jsx?

JSX is a syntax extension to JavaScript. It is used with React to describe what the user interface should look like. By using JSX, we can write HTML structures in the same file that contains JavaScript code.

<hr />

## What is dom?

Document Object Modal <br />
Document: Document is the file, say the html file<br />
Object: All the tags inside html file <br />
Modal: A tree like hirerichy structure that javascript creates.<br />

<hr />

## What is virtual dom?

In memory representation or virtual representation or light weight copy of real dom. When our application is rendered first time a first copy of dom is created, when there any update happens a second copy of virtual dom creates and both the copies compare with each other through diffing algorithm (Diffing is a heuristic algorithm), only updated values are sent to the first copy of virtual dom, meanwhile first copy is in the sync of real dom and then from first copy the real dom will be updated. (this process is called reconciliation)

<hr />

## What is diffing algorithm?

When the state of a component changes, React updates the virtual DOM tree. Once the virtual DOM has been updated, React then compares the current version of the virtual DOM with the previous version of the virtual DOM. This process is called “diffing”.

<hr />

## How virtual dom case is faster while still we are actually at the end updating in real dom, so why don't we simply update in real dom rather than creating the whole virtual dom and all the reconciliation procedure?

React follows batch update mechanism to update real dom, which increases perfomance. This means that updates to the real DOM are sent in batches, instead of sending updates for every single change in state. The repainting of the UI is the most expensive part, and React efficiently ensures that the real DOM receives only batched updates to repaint the UI.<br/>
Also react is not responsible for working with real dom that is the job of react dom library, react is a library which has to care about components(props, states, context, etc.).

<hr />

## <mark>Components</mark>

## Component in react?

Component are just chunks of codes that we create for reusing purposes, or we can use them for writting complex logics into small divisions of codes.

<hr />

## Higher order components?

Component that takes a component in the arguments and return a component.

<hr />

## An example for higher order component that you have used in your project?

Layout component

## Pure component?

Based on the concept of purity in functional programming paradigms, a function is said to be pure if it meets the following two conditions:

- Its return value is only determined by its input values
- Its return value is always the same for the same input values

<hr />

## Controlled vs unctrolled components?

**First Answer:**
Controlled: In React, controlled components refer to components that have their state and behavior controlled by the parent component. <br />
Uncontrolled: An uncontrolled functional component is a component that maintains its own internal state. <br />
**Second Answer:**
Controlled: Using states to manage the input
Uncontrolled: Using ref to manage the input

<hr />

# <mark>States and Props</mark>

## What is state?

The state is a built-in React object that is used to contain data or information about the component.

## Why we use state rather than normal javascript variables (var, let, const)?

States are responsible for rendering stuff, by using let, var and const on updation of data component will not render.

<hr />

## Difference between mutable and immutable states?

Immutable: Immutable state means its value cannot be changed once it’s created. <br />
Mutable: Value can be changed <br />

<hr />

## Difference between states and props?

States are mutable while props are immutable. <br />
State is owned locally and the component itself updates it. Props are owned and read-only by a parent

## What is one way data binding? Is two way data binding possible?

Send data from parent to child only.<br />
No 2 way data binding is not possible, we can use global state or states uplifting to solve the problem, but still two way binding is not possible.

<hr />

## How we will share data between different components?

Using props.

<hr />

## 13. Case: <br />

- We have 2 child components
- We have 1 parent components
- Take 2 states in parent component let say a,b
- Pass state a to first child, and b to second child
- Update state a, will second component render or not?
- How to avoid it?
- Using memo avoided the case, now I will pass setA to child 1 and setB to child 2 with the same scenario, will updating of "a" rerender child 2 component?
- How to avoid it?

**Solution:**

1. Yes, on state updating in the parent component all the childs will re-render.<br />
2. We can memoize our components to solve the re-rendering problem, memo is used for this we will make HOC by wrapping our component into memo.<br />
3. By passing, functions as the functions are objects in javascript, so it will create a new reference every time which is why even by using memo it will still cause re-rendering problem, to avoid this we will use useCallback hook.

<hr />

## How we can send data from child to parent or how we can achieve two way binding in react?

Not possible, we can use context hooks or redux for sharing data but still two way binding is not possible.

<hr />

# <mark>React Life Cycles</mark>

## What is render method in react?

As the name suggests it handles the rendering of your component to the UI. It happens during the mounting and updating of your component

## Is render method a life cycle method?

Yes, it is the most used life cycle method.

## Can you explain mounting, updating and unmounting of components?

Mounting – Birth of your component <br />
Update – Growth of your component <br />
Unmount – Death of your component <br />

## What is react fiber?

https://github.com/acdlite/react-fiber-architecture
