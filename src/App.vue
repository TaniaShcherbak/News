<template>
    <div class="main-container">
        <div class="header">
            <div class="title">
                <searchBar @searchQuerry="changeQuerry" />
                <h1>{{ pageTitle }}</h1>
            </div>
            <div>
                <navPanel @amountItemsOnPage="changeAmount" />
                <currencyConvert />
            </div>
        </div>

        <postPanel :newQuerry="newQ" :amount="amountPost" />
    </div>
</template>

<script>
import postPanel from "./components/PostBoard.vue";
import searchBar from "./components/search.vue";
import navPanel from "./components/NavPanel.vue";
import currencyConvert from "./components/Currensy.vue"
export default {
    name: "App",
    data() {
        return {
            newQ: "Apple",
            pageTitle: "LATEST NEWS HERE!!",
            amountPost: 6,
            pageTitle2: "",
        };
    },
    components: {
        postPanel,
        searchBar,
        navPanel,
        currencyConvert
    },
    methods: {
        changeQuerry(data) {
            this.newQ = data;
            data.trim() == ""
                ? (this.pageTitle = `LATEST NEWS HERE!!`)
                : (this.pageTitle = `LATEST NEWS ABOUT ${data}`);

        },
        changeAmount(data) {
            this.amountPost = data;
        },
    },
};
</script>
<style>
.header {
    width: 100vw;
    min-height: 400px;
    background: url(../public/headerbackground.png) no-repeat;
    background-size: 100vw auto;
}

.main-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 0px 100px;
}

h1 {
    color: rgb(219, 221, 253);
    font-size: 48px;
}
</style>
