## 1. What are signals in angulae?

Signals in angular 16 are a new way to manage asynchronous data flow in the framework. This provides simple reactive approach to handle data streams that can be used accross different components and services in an application. Signals are essentially observable streams of data that can be subscribed to and acted upon when new data is received.

## 2. Previous approach for asynchronous actions?

Before signals typically combination of observables and signal emitters were used to handle asynchronous data flows

## 3. How are signals different from previous approach?

Previous approach was complicated, signals is a more simpler way of doing it.
Signals are bi-directional, means they can be used to send and recieve data. Which makes two way communication easy.
Signals are more declarative, can be defined using simple syntex.
