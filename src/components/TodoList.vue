<script setup lang="ts">
import { ref } from 'vue'

interface Task{
    name: string
    fin: boolean
}

const tasks = ref<Task[]>([
    {name: "example",fin: true}
])

const newTaskName=ref('')

const addTask= ()=>{
    tasks.value.push({name: newTaskName.value,fin:false})
}
</script>

<template>
    <div>
        <h2>タスク</h2>
        <ul>
            <li v-for="task in tasks" :key="task.name">
                <div>タスク名:{{ task.name }}</div>
                <div v-if="task.fin">完了</div>
                <div v-else>未完</div>
                <button @click="task.fin=!task.fin">完了/未完切り替え</button>
            </li>
        </ul>
        <div>
            <label>
                タスク名
                <input v-model="newTaskName" type="text" />
            </label>
            <button @click="addTask">追加</button>
        </div>
    </div>
</template>