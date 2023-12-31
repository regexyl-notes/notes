title:: Notes: pomb.us Build Your Own React

- In the article: "node" refers to DOM elements, while "element" refers to React elements
- Concurrent mode: A rendering algorithm that allows for the browser to interrupt rendering of the DOM tree with urgent work that needs to be done asap. This helps keeps the webpage responsive and allows for an app that has a complex and large UI update to still process user inputs in real-time.
- `window.requestIdleCallback()`: A method that queues a function to be called during a browser's idle period, e.g. *when there's free time at the end of a frame* #help or when the user is inactive.
	- With each element as a "fiber", the rendering of these fibers are scheduled within the `requestIdleCallback` execution.
	- The `nextUnitOfWork` will be first set as the root fiber, and subsequently the element's children.