<template>
    <div class="main-container">
        <h1>{{ pageTitle }}</h1>
        <searchBar @searchQuerry="changeQuerry" />
        <navPanel @amountItemsOnPage="changeAmount"/>
        <postPanel :newQuerry=newQ :amount=amountPost />
    </div>
</template>

<script>
import postPanel from "./components/PostBoard.vue"
import searchBar from "./components/search.vue"
import navPanel from "./components/NavPanel.vue"
export default {
    name: "App",
    data() {
        return {
            newQ: "Apple",
            pageTitle: "LATEST NEWS HERE!!",
            amountPost:8,
        }
    },
    components: {
        postPanel,
        searchBar,
        navPanel
    },
    methods: {
        changeQuerry(data) {
            this.newQ=data;
            data.trim() == "" ? this.pageTitle = `LATEST NEWS HERE!!` : this.pageTitle = `LATEST NEWS ABOUT ${data}`;
        },
        changeAmount(data){
            this.amountPost=data;
        }
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