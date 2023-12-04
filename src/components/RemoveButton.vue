<template>
    <button @click="removeTodo"><i class="fa-solid fa-trash delete-button" style="color: #153266;"></i></button>
</template>

<script>
    export default {
        name: 'RemoveButton',
        methods: {
            removeTodo() {
                this.$emit('removeTodo')
            }
        },
        props: {
            todos: Array,
            todo: String,
        }
    }
</script>

<style scoped>
    button {
        background: transparent;
        border: none;
    }
    
    .delete-button {
        font-size: clamp(1.5rem, 0.0909rem + 3.6364vw, 2rem);
        /* font-weight: bold; */
    }
</style>