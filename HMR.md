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
