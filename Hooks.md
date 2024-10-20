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

HMR (Hot Module Replacement) is a feature provided by development tools like Webpack and used by frameworks such as Next.js to 
improve the developer experience by updating modules in real-time without a full page reload. It allows you to see the effects 
of code changes instantly during development.


HMR (Hot Module Replacement) is a feature provided by development tools like Webpack and used by frameworks such as Next.js to improve the developer experience by updating modules in real-time without a full page reload. It allows you to see the effects of code changes instantly during development.

How Does HMR Work?
When you change and save a file, the HMR system recompiles only the updated modules (instead of the entire application).
The updated modules are injected into the running app—the browser applies these changes immediately.
The page does not reload, so the app’s state is preserved, which makes development faster and smoother.

Why is HMR Useful?
Faster development cycle: No need to manually reload the page on every change.
State preservation: If you modify a component, the application state remains intact.
Instant feedback: You see the results of your changes immediately in the browser.

HMR Example in Next.js
Next.js uses HMR to let developers see their changes in real-time. If you update a component or page, it will reflect the changes immediately without a full page reload.

For example, if you modify the text inside a component, HMR ensures that only the affected module updates, not the entire page.

In React 18 and above, Strict Mode was enhanced to detect unexpected side effects. During development (not in production), React deliberately:
Mounts the component, runs useEffect → (Logs: "Component mounted!")
Unmounts the component.
Mounts it again and runs useEffect a second time to ensure your effects are safe and properly cleaned up.
This behavior is only present in development mode to help you catch side effects and ensure cleanup is correctly handled.
Should You Worry About This?
No, this double execution only happens in development mode for debugging purposes. In production, the component will mount only once, and useEffect will also run once.

