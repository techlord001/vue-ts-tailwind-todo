# Vue 3 + TypeScript + Vite + TailwindCSS TodoList

This project is a simple Todo List application built with Vue 3, TypeScript, and Tailwind CSS. It serves as a demonstration of how these technologies can be used together to build a modern, interactive web application.

## Project Overview

The Todo List application allows users to:

- Add new tasks
- Mark tasks as completed
- Delete tasks

Each task is represented by a Vue component, with its state managed by Vue's reactivity system. TypeScript is used to provide static typing for the components' props and state, improving code reliability and developer experience.

Tailwind CSS is used for styling the application. It provides utility classes that make it easy to build custom designs without leaving your HTML.

## Code Structure

The main parts of the application are:

- `App.vue`: This is the root component of the application. It contains the list of tasks and the form for adding new tasks.
- `Task.vue`: This is the component for individual tasks. It receives a task prop and emits events when the task is marked as completed or deleted.
- `main.ts`: This is the entry point of the application. It sets up Vue and mounts the root component to the DOM.
- `styles.css`: This file contains global styles and imports Tailwind CSS.

## Running the Project

To run the project:

1. Install dependencies with `npm install`
2. Start the development server with `npm run dev`
