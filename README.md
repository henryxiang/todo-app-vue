## Vue.js Todo App

### Getting Started

- Install vue-cli `npm install -g @vue/cli`
- Download and install [Visual Studio Code](https://code.visualstudio.com/)
- Install [vuejs/vetur plugin](https://github.com/vuejs/vetur)
- Create new Vue.js project `vue create -d todo-app-vue`

### Step 1: `git checkout step-1`

- Download CSS files from [todomvc-app-template](https://github.com/tastejs/todomvc-app-template) and copy them to `src/assets` folder
- Create TodoList.vue with template based on todomvc-app-template's index.html
- Update App.vue to render TodoList component

### Step 2: `git checkout step-2`

- Create `todos` object array in `data()` method
- Replace static todo list with dynamic rendering using `v-for` and `v-bind` directives

### Step 3: `git checkout step-3`

- Create TodoItem.vue to render individual todo list item
- Refactor TodoList.vue to compose template with TodoItem sub-component

### Step 4: `git checkout step-4`

- Bind form input to `nextItem` variable using `v-model` directive (two-way data binding)
- Add `keyup` event listener to input field
- Create callback function to handle `keyup` event and add new todo item

### Step 5: `git checkout step-5`

- Emit custom `delete` event when the delete link is clicked
- Add `delete` event listener to TodoItem tag
- Create callback functin to handle `delete` event and remove the specified todo item

### Step 6: `git checkout step-6`

- Emit custom `toggle` event when the checkbox is checked
- Add `toggle` event listener to TodoItem tag
- Create callback functin to handle `toggle` event and change the status of the specified todo item
