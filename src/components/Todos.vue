<template>
    <div class="todos">
        <input 
            type="text"
            v-model="newTodo"
            @keypress.enter="inputEntered"
            placeholder="Ajouter une tâche..."
        />
        <Transition name="switch" mode="out-in">
            <div v-if="todos && todos.length">
                <TransitionGroup tag="ul" name="list" appear>
                    <li 
                        v-for="todo in todos" 
                        :key="todo.id"
                        @click="emit('deleteTodo', todo.id)"
                    >
                        {{ todo.text }}
                    </li>
                </TransitionGroup>
            </div>
            <div v-else>Toutes les tâches sont terminées!</div>
        </Transition>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    todos: {
        type: Array
    }
})

const newTodo = ref();
const emit = defineEmits(['addTodo', 'deleteTodo', 'badValue']);

const inputEntered = () => {
    if(newTodo.value && newTodo.value.length > 0) {
        emit('addTodo', newTodo.value);
        newTodo.value = '';
    }
    else {
        emit('badValue');
    }
}
</script>

<style>

.todos {
    width: 400px;
    margin: 20px auto;
}

.todos input {
    width: 100%;
    padding: 12px;
    border: 1px solid #eee;
    border-radius: 10px;
    box-sizing: border-box;
    margin-bottom: 20px;
}

.todos ul {
    position: relative;
    padding: 0;
}

.todos li {
    list-style-type: none;
    display: block;
    margin-bottom: 10px;
    padding: 10px;
    background: white;
    box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    width: 100%;
    box-sizing: border-box;

    &:hover {
        cursor: pointer;
    }
}

.list-enter-from, .list-leave-to {
    opacity: 0;
    transform: scale(0.6);
}
.list-enter-active {
    transition: all 0.4s ease;
}
.list-leave-active {
    transition: all 0.4s ease;
    position: absolute;
}
.list-move {
    transition: all 0.3s ease;
}

.switch-enter-from, .switch-leave-to {
    opacity: 0;
    transform: translateY(20px);
}
.switch-enter-active, .switch-leave-active {
    transition: all 0.5s ease;
}
</style>