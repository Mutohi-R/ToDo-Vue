<template>
   <button @click="handleUpdate" ><i class="fa-solid fa-check update-button" style="color: #153266;"></i></button>
</template>

<script>
    export default {
        name: "UpdateButton",
        methods: {
            handleUpdate() {
                this.$emit('handleUpdate')
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
    
    .update-button {
        font-size: clamp(1.5rem, 0.0909rem + 3.6364vw, 2rem);
        /* font-weight: bold; */
    }
</style>