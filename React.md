## 🟢What is jsx?

JSX is a syntax extension to JavaScript. It is used with React to describe what the user interface should look like. By using JSX, we can write HTML structures in the same file that contains JavaScript code.

## What is dom?

Document Object Modal
Document: Document is the file, say the html file
Object: All the tags inside html file, say <div>, <h1>, <p>
Modal: A tree like hirerichy structure that javascript creates.

## What is virtual dom? (or a confusing way is to ask, what is reconciliation?)

In memory representation or virtual representation or light weight copy of real dom. When our application is rendered first time a first copy of dom is created, when there any update happens a second copy of virtual dom creates and both the copies compare with each other through diffing algorithm (Diffing is a heuristic algorithm), only updated values are sent to the first copy of virtual dom, meanwhile first copy is in the sync of real dom and then from first copy the real dom will be updated. (this process is called reconciliation)

## What is one way data binding?

Send data from parent to child only.

## How we will share data between different components?

Using props.

## How we can send data from child to parent or how we can achieve two way binding in react?

Not possible, we can use context hooks or redux for sharing data but still two way binding is not possible.

## Component is react?

Component are just chunks of codes that we create for reusing purposes, or we can use them for writting complex logics into small divisions of codes.

## Higher order components?

Component that takes a component in the arguments and return a component.

## An example for higher order component that you have used in your project?

Layout component

## What is state?

## Why we use state rather than normal javascript variables (var, let, const)?

## 🔴What is react fiber?

https://github.com/acdlite/react-fiber-architecture
