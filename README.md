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
