- Version 10.16.0
- Concepts
	- VNode
		- Seems to imply that there's different types of VNodes, see src/create-element.js L. 30 - "If a Component VNode, check for and apply defaultProps".
		- ```ts
		  export interface VNode<P = {}> extends preact.VNode<P> {
		  	// Redefine type here using our internal ComponentType type
		  	type: string | ComponentType<P>;
		  	props: P & { children: ComponentChildren };
		  	ref?: Ref<any> | null;
		  	_children: Array<VNode<any>> | null;
		  	_parent: VNode | null;
		  	_depth: number | null;
		  	/**
		  	 * The [first (for Fragments)] DOM child of a VNode
		  	 */
		  	_dom: PreactElement | null;
		  	/**
		  	 * The last dom child of a Fragment, or components that return a Fragment
		  	 */
		  	_nextDom: PreactElement | null;
		  	_component: Component | null;
		  	_hydrating: boolean | null;
		  	constructor: undefined;
		  	_original: number;
		  }
		  ```
	- Element
		- Can consist of a VNode, as seen from `createElement` returning a value of `createVNode`
	- Component
		-
- render
	- `render`
		- Questions
			- ?>> What's hydration mode? (L. 21 in src/render.js)
			- ?>> Why do you need to obtain reference to the previous tree if you want to be able to support calling `render()` multiple times on the same DOM node? (L. 23)
			- ?>> What exactly is a tree? Is it a VDom? Or is it made up of VNodes? Is there even a difference?
		- VNode is different from VDom
		- Fragment: `Fragment = props.children` (L. 88 in src/create-element.js)
- create-element
	- `createElement`
		- Questions
			- How is `type.defaultProps` initialized?