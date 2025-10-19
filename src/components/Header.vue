<script setup>
    import Wrapper from "./Wrapper.vue";
    import Logo from "./Logo.vue";

    const LINKS = ['Вступить в клуб', 'Деятельность клуба', 'Услуги', 'О нас'];
</script>

<template>
    <header>
        <Wrapper class="header">
            <Logo />
            <nav>
                <a v-for="e in LINKS" href="">{{ e }}</a>
            </nav>
        </Wrapper>
    </header>
</template>

<style scoped>
    header {
        background: black;
    }
    .header {
        align-items: center;
        justify-content: space-between;
        display: flex;
        padding: 4px 12px;
        gap: 12px;
    }
    nav {
        color: white;
        display: flex;
        gap: 12px;
    }
    a {
        color: white;
    }
    a:hover {
        opacity: 0.5;
    }
</style>
