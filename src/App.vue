<template>
    <div class="main-container">
        <h1>{{ pageTitle }}</h1>
        <searchBar @searchQuerry="changeQuerry" />
        <postPanel :newQuerry=newQ />
    </div>
</template>

<script>
import postPanel from "./components/PostBoard.vue"
import searchBar from "./components/search.vue"
export default {
    name: "App",
    data() {
        return {
            newQ: "Apple",
            pageTitle: "LATEST NEWS HERE!!",
        }
    },
    components: {
        postPanel,
        searchBar
    },
    methods: {
        changeQuerry(data) {
            this.newQ=data;
            data.trim() == "" ? this.pageTitle = `LATEST NEWS HERE!!` : this.pageTitle = `LATEST NEWS ABOUT ${data}`;
        }
    },
    computed: {
        computedValue() {
            return this.newQuerry;
        },
    },
}
</script>
<style>
.main-container{
    display: flex;
    flex-direction: column;
    align-items: center;
}


</style>