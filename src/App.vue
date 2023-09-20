<template>
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <PostComponent :post="{ name: '1 post', date: '12.01.2022' }" />
  <PostComponent @clickCounter="onPostClickCounter" :test="45" :id="2"/>
  <PostComponent @clickCounter="onPostClickCounter" :id="1" />
  <Counter :counter="globalCounter" /> -->
    <div>
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
            amountPost:8
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
        },
        changeAmount(data){
            this.amountPost=data;
        }
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

