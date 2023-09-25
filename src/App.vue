<template>
    <div class="main-container">
        <div class="header">
            <div class="title">
                <searchBar @searchQuerry="changeQuerry" />
                <h1>{{ pageTitle }}</h1>
            </div>
            <div class="navPanelBoard">                
                <weatherPanel />
                <currencyConvert />
            </div>
        </div>
        <hotPanel @hotSearch="changeQuerry"/>
        <postPanel :newQuerry="newQ" :amount="amountPost" />
        <navPanel @amountItemsOnPage="changeAmount" />
    </div>
</template>

<script>
import postPanel from "./components/PostBoard.vue";
import searchBar from "./components/search.vue";
import navPanel from "./components/NavPanel.vue";
import currencyConvert from "./components/Currensy.vue"
import weatherPanel from "./components/Weather.vue"
import hotPanel from "./components/hotPanel.vue"
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
        currencyConvert,
        weatherPanel,
        hotPanel
    },
    methods: {
        changeQuerry(data) {
            this.newQ = data;
            data.trim() == ""
                ? (this.pageTitle = `LATEST NEWS HERE!!`)
                : (this.pageTitle = `LATEST NEWS ABOUT ${data}`.toUpperCase());

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
    font-family: 'Roboto';
}

.title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 0px 100px;
}

h1 {
    color: white;
    font-size: 48px;
    background-color: brown;
    padding: 10px;
    border-radius: 5px;
}
.navPanelBoard {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding: 0px 100px;
    margin-top: 10px;
}
</style>
