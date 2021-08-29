# Interview Answers

Be prepared to demonstrate your understanding of this week's concepts by answering questions on the following topics. These will not be counted as a part of your sprint score but will be helpful for preparing you for your endorsement interview, and enhancing overall understanding.

1. What problem does the context API help solve?

   - Context API helps to greatly limit prop drilling by allowing props/state data to be passed directly to the component that needs it rather than having to drill them through intermediaries in the component tree. For example, a top level App component can pass relevent state data directly to a grandchild component instead of having to prop drill through a child component that doesn't need it first before getting to the grandchild.

2. In your own words, describe `actions`, `reducers` and the `store` and their role in Redux. What does each piece do? Why is the store known as a 'single source of truth' in a redux application?

   - The store is the state object in redux. It holds all the global state data for an entire application. It is the single source of truth because all of the state data is in one place. Any of its properties can be referenced by any component, and changes that are made to its property values can be triggered by any component but the change that occurs in the centralized store. This way, if a state value is updated, that update happens application wide.
   - actions are just objects with a type property and a payload property. Action creators are functions that construct the action objects where specific payload data can be passed in as an argument before being dispatched to the reducer. Once at the reducer the action type tells the reducer which case statement to trigger and the payload provides the data necessary for state updates.
   - reducers are pure functions that take state (the current store), and an action object as arguments and return an updated state. Inside the reducer is as many switch cases as are needed to achieve desired state updates in the application. The switch cases are triggered by the action type passed in and they return a copy of the state object and may update specific state property values with or without a payload of data provided by the action object.

3. What does `redux-thunk` allow us to do? How does it change our `action-creators`?

   - redux-thunk is a piece of middleware that allows us to perform async actions before an action makes its way to the reducer. This way, data that is needed for a state change that comes via an axios request can be put into the action object's payload before it triggers the corresponding case in the reducer. It changes the action creator by making it a function that returns another function (a thunk), rather than just a function that returns the action object. Typically the function the thunk returns passes in dispatch as an argument and is used to dispatch multiple actions asynchronously depending on the outcome of the asynchronous action.

4. What is your favorite state management system you've learned and this sprint? Please explain why!
   - I think redux is great, when I started to 'get it' I finally felt like I could attempt to build something big and real. I always had something in the back of my mind when we were just using state hooks and component level state that told me it would be nearly impossible to manage all those slices of state at scale.
