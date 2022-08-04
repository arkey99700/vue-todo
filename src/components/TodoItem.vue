<template>
    <li class="list-group-item list-group-item-action d-flex justify-content-between align-items-center">
        <span @input="this.$parent.updateTodo(this.id, this.$el.textContent)" class="d-block" contenteditable="true">{{ text }}</span>
        <button @click="this.$parent.removeTodo(this.id)" class="btn btn-close"></button>
    </li>
    
</template>

<script>
export default {
    name: "TodoItem",
    props: ["id", "text"]
}
</script>

<style>
    span[contenteditable="true"] {
        width: 95%;
        z-index: 1;
    }

    span[contenteditable="true"]:empty::before {
        opacity: 0.5;

        cursor: text;
        content: "Enter some text";
    }

    span[contenteditable="true"]:focus {
        outline: none
    }
</style>