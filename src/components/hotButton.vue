<template>
    <div>
        <button name="title" @click="hotQuerry">
            {{ hotButton.title }}
        </button>
    </div>
</template>
<script>
export default {
    name: 'hotButton',
    props: {
        hotButton: {},
    },
    methods: {
        hotQuerry() {
            this.$emit("hotSearch",this.hotButton.title);
        }
    }
}
</script>
<style>
button{
    background-color:inherit;
    color:white;
    border:none;
}
</style>