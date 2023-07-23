- Event handlers are passed instances of `SyntheticEvent`, a cross-browser wrapper around the browser's native event.
- `SyntheticEvent` has the same interface as the browser's native event, including `stopPropagation()` and `preventDefault()`.
- The synthetic events may not directly map to the browser's native events.
- E.g. React's `onMouseLeave` points to a native `mouseout` event (which can be seen if you access `event.nativeEvent`).
- Why is this implemented?
	- Provides consistency by normalizing events across browsers and systems so that they have the same properties.
	- Prior to React 17: `SyntheticEvent` objects were pooled and all properties would be nullified after the event handler has been called, so something like this wouldn't work:
		- ```js
		  function handleChange(e) {
		    // This won't work because the event object gets reused.
		    setTimeout(() => {
		      console.log(e.target.value); // Too late, function would have been exited
		    }, 100);
		  }
		  ```
- Why was event pooling removed from React 17?
-