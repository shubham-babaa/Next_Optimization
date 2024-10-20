In React 18 and above, Strict Mode was enhanced to detect unexpected side effects. During development (not in production), React deliberately:

Mounts the component, runs useEffect → (Logs: "Component mounted!")
Unmounts the component.
Mounts it again and runs useEffect a second time to ensure your effects are safe and properly cleaned up.
This behavior is only present in development mode to help you catch side effects and ensure cleanup is correctly handled.

Should You Worry About This?
No, this double execution only happens in development mode for debugging purposes. In production, the component will mount only once, and useEffect will also run once.

