<template>
    <div class="hotPanel">
        <hotButton :hotButton="{ title: 'Sport' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Weather' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Culture' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Politics' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Travell' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Business' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Health' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Future' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'Tech' }" @hotSearch="onHotSearch" />
        <hotButton :hotButton="{ title: 'World' }" @hotSearch="onHotSearch" />
    </div>
</template>
<script>
import hotButton from './hotButton.vue'
export default {
    name: "hotPanel",
    components: {
        hotButton
    },
    // watch: {
    //     hotSearch: 'onHotSearch'
    // },
    methods: {
        onHotSearch(data) {
            this.$emit('hotSearch', data)
        }
    }

}
</script>
<style>
.hotPanel {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    height: 100px;
    border: 2px solid darkgrey;
    width: 100vw;
    /* background-color: gray; */
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