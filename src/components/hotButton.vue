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
.hotPanel button {
    width: 140px;
    height: 40px;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 700;
    font-size: 20px;
}

.hotPanel button:hover {
    color: brown;
}
</style>
