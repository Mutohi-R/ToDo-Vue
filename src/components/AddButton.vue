<template>
        <button @click="addTodo"><i class="fa-regular fa-square-plus add-button" style="color: #153266;"></i></button>
</template>

<script>
    export default {
        name: 'AddButton',
        methods: {
            addTodo() {
                this.$emit('addMyTodo');
            }
        }
    }
</script>

<style scoped>
    button {
        background: transparent;
        border: none;
    }
    
    .add-button {
        font-size: clamp(1.5rem, 0.0909rem + 3.6364vw, 2rem);
    }

</style>