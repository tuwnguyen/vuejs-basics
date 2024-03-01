# vue-basics

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Purposes of this project
Learning Vuejs from Nutshell


### Vue3 Migration Guide
See [Filters](https://v3-migration.vuejs.org/breaking-changes/filters.html)


### Differences between Composition and Option API
See [Diff](https://www.linkedin.com/pulse/vue-3-options-api-vs-composition-whats-difference-md-najmul-hasan/)

### Option API
- hooks:
  - mounted()

- computed properties
  - A computed property automatically tracks its reactive dependencies. Vue is aware that the computation of computed functions depends on state or ever value, so it will update any bindings that depend on compute function when state changes.

- watch property
  - [watch](https://vuejs.org/api/options-state.html#watch)

- create custom events
  - [event](https://vuejs.org/api/options-state.html#emits)
  - Declare the custom events emitted by the component.
  ```js
  $emit: with $ is public property
  ```

### Composition API
- [Migrate from option api to composition api](https://dev.to/nicolasmontielf/migrate-option-api-to-composition-api-on-vue3-4o3p)


### Concepts
- 2ways binding
- LifeCycle
  - [lifecycle hook](https://vuejs.org/guide/essentials/lifecycle.html)
  - [created() hook](https://vuejs.org/api/options-lifecycle.html#created)
    - Called after the instance has finished processing all state-related options.
    
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

- ref: 
  - Refer to element

- conditional rendering: 
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

- props:
  - [props doc](https://vuejs.org/guide/components/props.html)
  - Convey data from parent comp to child comp
  - Props are read only
  - dynamic and static props
  - How to change props from child comp: using event function in props 
  ```html
  <child-comp :change-prop-event="(value) => prop = value"><child-comp>
  ```

- filters:
  - format data before rendering 
  - local and global filters

### Advanced-Concepts
#### Components In-Depth
  - [Slots](https://vuejs.org/guide/components/slots.html#slots)

### Vue Router
- [Docs](https://router.vuejs.org/introduction.html)
- route params
- router's active class
- nesting routes

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