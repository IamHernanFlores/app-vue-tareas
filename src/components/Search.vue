<template>
    <div id="search-container">
        Buscar tarea 🔍
        <input type="text" v-model="query" v-on:input="$emit('query-change', query)" title="Buscar tarea">
    </div>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return {
            query: ''
        }
    }
}
</script>

<style scoped>
    #search-container{
            width: 583px;
    margin: 0px auto;
    text-align: center;
    font-family: sans-serif;
    }

    input{
        padding: 10px;
        width: 100%;
        outline: none;
            border-radius: 10px;

    }
</style>