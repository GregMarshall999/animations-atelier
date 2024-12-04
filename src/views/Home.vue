<template>
    <div class="home">
        <Transition name="toast">
            <Toast v-if="showToast" />
        </Transition>
        <Todos 
            :todos="todos"
            @add-todo="newTodo => addTodo(newTodo)"
            @delete-todo="tId => removeTodo(tId)"
            @bad-value="triggerToast"
        />
    </div>
</template>

<script setup>
import Toast from '@/components/Toast.vue';
import Todos from '@/components/Todos.vue';
import { ref } from 'vue';

var id = 1;
const todos = ref([
    { text: 'Faire le lit', id: id++ },
    { text: 'Préparer le petit dej', id: id++ }
]);

const addTodo = newTodo => {
    todos.value = [{ text: newTodo, id: id++ }, ...todos.value]
}
const removeTodo = todoId => {
    todos.value = todos.value.filter(t => t.id != todoId);
}

const showToast = ref(false);
const triggerToast = () => {
    showToast.value = true;
    setTimeout(() => showToast.value = false, 3000);
}

const showD = ref(false);
</script>

<style scoped>

.home {
    display: flex;
    justify-content: center;
}

.toast-leave-to {
    opacity: 0;
    transform: translateY(-60px);
}
.toast-leave-active {
    transition: all 0.3s ease;
}

.toast-enter-active {
    animation: wobble 0.5s ease;
}
@keyframes wobble {
    0% {
        opacity: 0;
        transform: translateY(-60px);
    } 
    50% {
        opacity: 1;
        transform: translateY(0);
    }
    60% { transform: translateX(8px); }
    70% { transform: translateX(-8px); }
    80% { transform: translateX(4px); }
    90% { transform: translateX(-4px); }
    100% { transform: translateX(0); }
}

</style>