<template>
    <section v-if="currentFilm">
        <h2>{{ currentFilm.title }}</h2>
        <p>Relese Date: {{ currentFilm.release_date }}</p>
        <p>Director: {{ currentFilm.director }}</p>
        <p>Producer: {{ currentFilm.producer }}</p>
        <p>Plot: {{ currentFilm.description }}</p>
    </section>
</template>

<script>
export default {
    name: 'selected-film',
    props: ['currentFilm']
}
</script>

<style>

</style>