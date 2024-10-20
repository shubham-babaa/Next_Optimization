1)UseState
The useState hook in React allows you to manage state in a functional component. 
It gives your component the ability to track and update variables over time 
(like user input or the status of UI elements) while ensuring the UI re-renders when the state changes.


2)UseEffect

The useEffect hook in React is used to perform side effects in functional components. These side effects can include things like:
Fetching data from APIs
Subscribing to events
Manipulating the DOM
Setting up timers or intervals
Cleanup operations when a component unmounts

useEffect(() => {
  // Side effect logic
  return () => {
    // Optional cleanup logic
  };
}, [dependencies]);

When useEffect Runs:
On Initial Render: Runs after the component is rendered for the first time.
On Dependency Change: If a value inside the dependency array changes, the effect will re-run.
On Component Unmount: If a cleanup function is returned, it runs when the component unmounts or before the effect runs again.


1. Page Component Doesn’t Unmount in Next.js Apps Easily
Since you're using this component as a page in Next.js, it remains mounted as long as the user stays on the page.
In Next.js, page-level components typically don’t unmount unless the user
navigates away to another page. Therefore, the cleanup function inside useEffect won't
be triggered unless the page component is removed or replaced.


When will the cleanup run?
If the user navigates to a different page in your Next.js app.
If Hot Module Replacement (HMR) occurs (in development mode).


3)useRef Hook in React – Explained in Detail
The useRef hook is a built-in hook in React that allows you to create and manage mutable references that persist across component re-renders.
Unlike state changes (which cause re-renders), changing a reference via useRef does not trigger a re-render.

This makes useRef useful for accessing DOM elements, storing values that don’t trigger re-renders, or creating instance variables.

const refContainer = useRef(initialValue);
initialValue: Optional. It defines the initial value of the ref object.
Returns: A ref object with the shape { current: initialValue }.

When to Use useRef?
Accessing or Manipulating DOM Elements
Tracking Mutable Variables without Re-renders (like timers or previous values)
Persisting Values between Renders (instance variables in functional components)

What is Mutation?
In programming, mutation refers to the change of an object or data structure's state after it has been created.
A mutation modifies the original object or value directly, rather than creating a new copy. 
In React and functional programming, mutating state or data directly is generally discouraged because it can lead to unpredictable behavior, bugs, and side effects.


