<template>
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <PostComponent :post="{ name: '1 post', date: '12.01.2022' }" />
  <PostComponent @clickCounter="onPostClickCounter" :test="45" :id="2"/>
  <PostComponent @clickCounter="onPostClickCounter" :id="1" />
  <Counter :counter="globalCounter" /> -->
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
// import HelloWorld from "./components/HelloWorld.vue";
// import PostComponent from "./components/Post.vue";
// import Counter from "./components/Counter.vue"
// export default {
//   name: "App",
//   components: {
//     HelloWorld,
//     PostComponent,
//     Counter
//   },
//   data() {
//     return {
//       globalCounter: 0,
//     }
//   },
//   methods: {
//     onPostClickCounter(counter, id) {
//       this.globalCounter=counter;
//     }
//   }
// };
</script>
<style>
.main-container{
    display: flex;
    flex-direction: column;
    align-items: center;
}


</style>