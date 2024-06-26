# Documentation for Vuejs

### Roadmap
See [Slide](https://roadmap.sh/vue)

### Cool things in Vue3
See [Slide](https://docs.google.com/presentation/d/12xGb9M4O9JO4niKSYsm6OtbWz2zI_R7VlhR0qro-zow/edit#slide=id.p)

### Differences between Composition and Option API
See [Diff](https://www.linkedin.com/pulse/vue-3-options-api-vs-composition-whats-difference-md-najmul-hasan/)

---
### Composition API
- [Migrate from option api to composition api](https://dev.to/nicolasmontielf/migrate-option-api-to-composition-api-on-vue3-4o3p)

- Lifecycle Hooks
  - `onMounted()`
    -: is used for executing logic or actions after a comp has been mounted to the DOM. This hook is useful for tasks should occur once, comp is ready to interact with the user, such as `fetching data, setting up the events listeners, performing initial calculations`
...

- Template Ref(Ref on component)
  - Using `defineExpose()` to parent component can access child components because when child comp using `<script setup>`, component private by default in that time.

---
### Concepts
- 2ways binding
  
- Binding:
   - value binding
   - property binding(attribute binding):
      `v-bind:attr` ==> new way `:attr`
   - dynamic binding
      ```js
      const imageInfo = {
        src: 'http://images.google.com/',
        alt: 'GG image',
        width: 400,
        height: 500
      }
      ...
      <image :="imageInfo"/>
      ```
- Styling
  - Global style
  - Local style (`<style scoped>`)
  - Module style
    - `<style module>` uses CSS Modules, which creates isolated style classes that cannot be used in other components unless explicitly imported. In another component, we can use styles from module by `$store` object
    - 

- Model: Connection and create 2way binding between the data in component and the input fields
  v-model

- Event handling:
  - Catch events from elements:
    ```
    v-on:event => @event="{function()}"
    ```
- Prevent default event
  - Cancel default event of this element

- [Template Ref](https://vuejs.org/guide/essentials/template-refs.html#template-refs): 
  -: is a way to create a **reference to a child** component, element, or a DOM element within a template. This allows you to access and manipulate the referenced object directly in your component's logic.(Refer to element)
  - Basic ref, function ref, ref on component()

- Conditional Rendering: 
  ```js
  v-show, v-hide, v-if, v-else-if, v-else (v-show: Vue still keep visibility(disabled) of v-show on the DOM, opposed to v-if) 
  //example for v-if, v-else-if
  const isTrue = true
  ...
  <p v-if="isTrue">This will show</p>
  <p v-else-if="isTrue">This will show</p>

  '===> just show the 1st p tag, because v-if just show the 1st if it already true'
  ```

- List rendering: 
  ```js
  v-for
  : not only iterate the array, nested array, but also an object or nested object
  <ul v-for="({game, genre, date}, index) in object">
    <li>{{genre}}</li>
    <li v-for="(property, i) in game">{{property}}</li>
  </ul>
  ```

- Methods: 
  - functions of vue object

- Watch: 
  - tracking changes of data
  - `watch(source, callback, options)`
    - source: Ref(), Reactive object, array, getter function


- Props:
  - [props doc](https://vuejs.org/guide/components/props.html)
  - Convey data from parent comp to child comp
  - Props are read only
  - Dynamic and static props
  - Props validation and default values
  - How to change props from child comp: using event function in props 
  ```html
  <child-comp :change-prop-event="(value) => prop = value"><child-comp>
  ```
- Provide & inject (Dependency Injection)
  - Parent component want to convey data to child components
  - `import { provide, inject } from 'vue'`

- filters:
  - format data before rendering 
  - local and global filters

- [Dynamic Component](https://vuejs.org/guide/essentials/component-basics.html#dynamic-components)
  - : refer to the ability to dynamically switch between different components based on certain conditions or user interaction.
  - `<component :is="FirstComponent">`
---
### Advanced-Concepts
#### Components In-Depth
  - [Slots](https://vuejs.org/guide/components/slots.html#slots)
  - : a slot is like a *space in a component* where you can put different things. Allow to create reusable components that can accept different content while maintaining a consistent structure.
  - Fallback/Default content in slot
  - Named slots: is a way to assign a specific name to a slot in a component.

  - [Async Components](https://vuejs.org/guide/components/async.html#async-components)
  - : is a feature that allows you to load a component asynchronously, meaning the components is **loaded and renderd when it's needed**
  - `defineAsyncComponent()`: used to create async components, which can be helpful for improving the initial loading performance of your application by deffering the loading of certain components until they are actually needed. In addition, it reduce the size of your initial bundle and improve the performance of your web application, especially for large-scale applications with numerous components.

  - [Fallthough Attributes](https://vuejs.org/guide/components/attrs.html)
  - : refers to attributes that are not recognized by Vue's component system and are passed through to the underlying DOM element. These attributes are not handled by Vue's reactivity system and are not reactive. They are simply passed through to the DOM element and can be used for any purpose that is supported by the DOM element.

#### Reusability
  - [Composables](https://vuejs.org/guide/reusability/composables.html)
  - : is a function or set of functions that encapsulate a piece of logic and can be composed together to build the functionality of a Vue component. **reusable and shareable** to manage complex logic and behavior in a Vue application
  - `use` prefix, ex: `useCounter()`

  - [Custom Directive](https://vuejs.org/guide/reusability/custom-directives.html)
  - : allow to define your own behavior that can be applied to elements in the template.

#### Scaling up
  - [Single-File Components](https://vuejs.org/guide/scaling-up/sfc.html)
  - : ???
  - [Server-Side Rendering](https://vuejs.org/guide/scaling-up/ssr.html)
  - : ???
---
### Vue Router
- [Docs](https://router.vuejs.org/introduction.html)
- route params
- router's active class
- nesting routes

---
### Vuex
- [Best practices](https://dev.to/timothyokooboh/vuex-best-practices-45dd)

- [Examples](https://github.com/vuejs/vuex/tree/main/examples)

- State
  - Single state tree

- Getters
  - Property-style access
  - Method-style access

- Mutations
  - `commit` with payload
  - mutations must be synchronous

- Actions
  - handle asynchronous operations
  - `context` argument: obj store hien tai
  - `commit`: call mutation
  - `dispatch`: call aciton

- Modules
  - Namspacing and nested modules
  - Dynamic module registration

- Mapping in Vuex
  - [Doc](https://viblo.asia/p/mapping-hoat-dong-nhu-the-nao-trong-vuex-djeZ1zL8lWz)
  ```js
  - mapState()
  - mapGetters()
  - mapMutations()
  - mapActions()
  ```

- Advanced
  - Plugins??
  - Strict mode
  ...

- How to mutate state of Vuex store in form component
  - [Link](https://vuex.vuejs.org/guide/forms.html)

---
### Others modules use with VUE
  - [More modules should be aware of](https://browsee.io/blog/10-vue-js-npm-modules-that-you-should-be-aware-of/)

  - `vue-i18n`
    . [Guide/API](https://kazupon.github.io/vue-i18n/started.html)
  - `vue-spinner`
    . [Guide](https://github.com/greyby/vue-spinner/tree/master)
  - `vue-loader`
    - is loader for webpack that allows you to author Vue components in a format called Single-File Components (SFCs)
    . [Guide](https://vue-loader.vuejs.org/guide/)
  - `vue-composable`
    - [Doc](https://pikax.me/vue-composable/composable/)
    - is a library that aims to provide a wide range of real-world composable functions for Vue.js applications. These composable functions are designed to encapsulate and reuse stateful logic using Vue's Composition API. 

  - Pinia
    - [Docs](https://pinia.vuejs.org/introduction.html)