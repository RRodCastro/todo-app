# todo-app

This is a simple Vue.js todo list app designed to help you learn the fundamentals of Vue.js, including template syntax, reactivity, style bindings, conditional rendering, list rendering, event handling, lifecycle hooks, props, events, and the v-model directive. The app uses the Composition API for structuring components.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```
### Features

- Create new todo items
- Delete todo items
- Mark todo items as completed
- Fetch todo items from a dummy API

### Composition API Usage

- Setup Function: Each component's setup function contains the component's logic, reactivity, and data.

- Reactivity: The ref and reactive functions are used to create reactive data properties.

- Lifecycle Hooks: The onMounted hook is used for lifecycle management.

- Event Handling: Event handlers are defined within the setup function using the @ syntax.

- Props: The props option allows passing data from parent to child components.

- v-model Directive: The v-model directive is used for two-way data binding.

