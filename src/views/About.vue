<template>
    <div class="about">
        <Transition
            appear
            @before-enter="beforeEnter"
            @enter="enter"
            @after-enter="afterEnter"
        >
            <h1>A Propos</h1>
        </Transition>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    </div>
</template>

<script setup>
import gsap from 'gsap';

const beforeEnter = e => {
    console.log('beforeEnter', e);

    e.style.transform = 'translateY(-60px)';
    e.style.opacity = 0;
};

const enter = (e, done) => {
    console.log('enter', e);

    gsap.to(e, {
        duration: 1, 
        y: 0,
        opacity: 1, 
        ease: 'bounce.out', 
        onComplete: done
    });
};

const afterEnter = e => {
    console.log('afterEnter', e);
};

</script>

<style scoped>
.about {
    max-width: 600px;
    margin: 20px auto;
}
</style>