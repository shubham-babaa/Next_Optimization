useLayoutEffect Hook
The useLayoutEffect hook is similar to useEffect, but it fires synchronously after all DOM mutations. 
This means that it runs after the browser has painted the changes to the DOM,
but before the screen is updated. It's useful for operations that need to read layout from the DOM and synchronously re-render.

useLayoutEffect(() => {
  // Your code here
  return () => {
    // Cleanup function (optional)
  };
}, [dependencies]);


When to Use
When you need to measure the DOM elements (like width, height, position).
When you want to perform updates that need to happen before the browser repaints the screen.
