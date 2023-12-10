<template>
    <div class="container">
        <h1 class="text-2xl font-bold">Todo List</h1>
        <input type="text" v-model="newTask" @keyup.enter="addTask" class="input" placeholder="Add a new task...">
        <ul>
            <li v-for="task in tasks" :key="task.id">
                {{ task.title }}
            </li>
        </ul>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

interface Task {
    id: number;
    title: string;
}

export default defineComponent({
    setup () {
        const tasks = ref<Task[]>([]);
        const newTask = ref('');

        const addTask = () => {
            if (newTask.value.trim()) {
                tasks.value.push({
                    id: Date.now(),
                    title: newTask.value,
                });
                newTask.value = '';
            }
        };

        return { tasks, newTask, addTask };
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
</style>