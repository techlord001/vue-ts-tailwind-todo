<template>
    <div class="container">
        <h1 class="text-2xl font-bold">Todo List</h1>
        <input type="text" v-model="newTask" @keyup.enter="addTask" class="input" placeholder="Add a new task...">
        <ul>
            <li v-for="task in tasks" :key="task.id" :class="{ 'completed': task.completed }">
                {{ task.title }}
                <input type="checkbox" v-model="task.completed">
                <button class="delete-button ml-2" @click="deleteTask(task)">X</button>
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

interface Task {
    id: number;
    title: string;
    completed: boolean;
}

export default defineComponent({
    setup() {
        const tasks = ref<Task[]>([]);
        const newTask = ref('');

        const addTask = () => {
            if (newTask.value.trim()) {
                tasks.value.push({
                    id: Date.now(),
                    title: newTask.value,
                    completed: false,
                });
                newTask.value = '';
            }
        };

        const deleteTask = (task: Task) => {
            const index = tasks.value.indexOf(task);
            if (index !== -1) {
                tasks.value.splice(index, 1);
            }
        };

        const toggleCompletion = (task: Task) => {
            task.completed = !task.completed;
        };

        return { tasks, newTask, addTask, deleteTask, toggleCompletion };
    },
});
</script>

<style scoped lang="scss">
.container {
    @apply p-5 max-w-lg mx-auto;
}

.input {
    @apply bg-gray-200 p-2 rounded mb-3 w-full;
}

.completed {
    @apply line-through text-gray-500;
}

.delete-button {
    @apply bg-red-500 text-white rounded w-5 h-5 text-center text-sm cursor-pointer;
}
</style>