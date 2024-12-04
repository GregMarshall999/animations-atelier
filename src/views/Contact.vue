<template>
    <div class="contact">
        <h1>Contact</h1>
        <TransitionGroup 
            tag="ul"
            appear
            @before-enter="init"
            @enter="start"
        >
            <li 
                v-for="(icon, index) in icons" 
                :key="icon.name"
                :data-index="index"
            >
                <span class="material-icons">{{ icon.name }}</span>
                <div>{{ icon.text }}</div>
            </li>
        </TransitionGroup>
    </div>
</template>

<script setup>
import gsap from 'gsap';
import { ref } from 'vue';

const icons = ref([
    { name: 'alternate_email', text: 'par email' },
    { name: 'local_phone', text: 'par telephone' },
    { name: 'local_post_office', text: 'par poste' },
    { name: 'local_fire_department', text: 'par signaux de fumée' }
]);

const init = e => {
    e.style.opacity = 0;
    e.style.transform = 'translateY(100px)';
}
const start = e => {
    gsap.to(e, {
        opacity: 1, 
        y: 0, 
        duration: 0.8, 
        delay: e.dataset.index * 0.2
    });
}
</script>

<style scoped>

.contact ul {
    padding: 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    max-width: 400px;
    margin: 60px auto;
}

.contact li {
    list-style-type: none;
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    line-height: 1.5em;
}

</style>