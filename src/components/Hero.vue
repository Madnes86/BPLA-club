<script setup lang="ts">
    import { ref } from 'vue';
    import Button from './Button.vue';
    import IconArrow from './icons/IconArrow.vue';

    const SLIDES = [
        'slide-1.png',
        'slide-2.png',
        'slide-3.png'
    ];
    let activeSlide = ref<number>(0);

    function getPosition(i: number) {
        const position = (i - activeSlide.value) * 100;
        return `translateX(${position}%)`;
    }
    function prevSlide() {
        if (activeSlide.value > 0) activeSlide.value--;
    }
    function nextSlide() {
        if (activeSlide.value < SLIDES.length -1) activeSlide.value++;
    }    
</script>

<template>
    <div class="slider">
        <div class="contener">
            <Button @click="prevSlide" :style="{left: '5%'}">
                <template #icon>
                    <IconArrow :size="32"/>
                </template>
            </Button>
            <img v-for="(slide, i) in SLIDES" 
                :src="slide" 
                :style="{ transform: getPosition(i), visibility: `${i === activeSlide ? 'visible' : 'hidden'}` }" 
                :alt="i.toString()" 
                :key="i" 
            >
            <Button @click="nextSlide" :style="{right: '5%'}">
               <template #icon>
                   <IconArrow :size="32" :style="{transform: 'rotate(180deg)'}"/>
               </template>
           </Button>
        </div>
    </div>
</template>

<style scoped>
    .slider {
        align-items: center;
        display: flex;
        padding: 24px;
        width: 100%;
        gap: 12px;
    }
    .contener {
        position: relative;
        width: 100%;
        height: 400px;
        overflow: hidden;
    }
    img {
        position: absolute;
        visibility: hidden;
        height: 100%;
        width: 100%;
        object-fit: cover;
        transition: all 0.5s ease;
        z-index: -1;
    }
    button {
        background: black;
        border-radius: 50%;
        border: 0px;
        color: white;
        cursor: pointer;
        opacity: 0.7;
        padding: 8px;
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
    }
    button:hover {
        opacity: 1;
        transition: all 0.5s ease;
    }
    button:active {
        opacity: 0.7;
        transition: all 0.5s ease;
    }
</style>