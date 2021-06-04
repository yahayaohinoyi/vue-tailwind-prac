<template>
    <button @click="onClick()" class="w-20 h-8 text-sm text-white bg-green-700 rounded-sm" :style="{background: color}"> 
        {{text}}
    </button>
</template>

<script>
    export default {
        name: "Button",
        props: {
            title: String,
            color: String,
            text: String
        },
        methods: {
            onClick() {
                this.$emit('click-add-btn')
            }
        }
    }
</script>
