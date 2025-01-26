# Vue.js Learning Dashboard

This project is a dashboard application designed to demonstrate core features and concepts of Vue.js during the learning process.

## Features

### 1. Authentication
- **Sign In**
  - Login using email and password
  - Form validation
  - Display error messages
  
- **Sign Up**
  - Register with username, email, and password
  - Password matching validation
  - Form validation
  - Display error messages

### 2. Todo List
- Add new tasks
- Delete tasks
- Mark tasks as completed
- Display the count of completed tasks
- Handle empty list state

### 3. Vue.js Features

#### Event Modifiers
- `@keyup.enter`: Use the Enter key to add new tasks
- `@click.stop`: Prevent event propagation on the delete button

#### Two-Way Data Binding
- Usage of `v-model`:
  - Form inputs
  - Todo input field
  - Checkbox states

#### Conditional Rendering
- `v-if`: Display error messages and handle empty list states
- Toggle between login and registration forms
- Display content based on user session status

#### List Rendering
- `v-for`: Render the todo list
- Manage unique keys
- Filter the list

#### Computed Properties
- Calculate the number of completed tasks

## Styling Features
- Responsive design
- Dark mode support
- Modern UI components
- Transition animations
- Interactive buttons and form elements

## Project Structure
- Vue 3 Composition API
- TypeScript support
- Vite build tool
- Component-based architecture
- Modular CSS
