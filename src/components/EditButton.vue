<template>
    <button @click="editTodo" ><i class="fa-solid fa-pen edit-button" style="color: #153266;"></i></button>
</template>

<script>
    export default {
        name: 'EditButton',
        methods: {
            editTodo() {
                this.$emit('editTodo')
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
    
    .edit-button {
        font-size: clamp(1.5rem, 0.0909rem + 3.6364vw, 2rem);
        /* font-weight: bold; */
    }
</style>