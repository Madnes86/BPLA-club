<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Wrapper from './components/Wrapper.vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
</script>

<template>
    <Header />
    <Wrapper>
        <Hero />
    </Wrapper>
</template>

<style></style>
