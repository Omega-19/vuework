<template>
<h1>{{ msg }}</h1>
<h2>{{ sms }}</h2>
<p class="Titre">{{ title }}</p>
<!-- <button ref="alert">Alert message</button> -->
</template>

<script setup>
    const msg = "Mes exercices";
    const sms = "Rendez moi dynamique !😎";
    let title = "I'm happy to learn vue";
    // this.refs.innerHTML = "Je suis parfait"
</script>

<style>
    .Titre{
        background-color: orange;
        color: black;
        font-style: italic;
        font-weight: 600;
    }
</style>