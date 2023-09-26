<template>
    <div class="panel">
        <div v-if="posts" class="post-board">
            <newsPost v-for="(index, i) in totalDisplayedPosts" :key="i" :postinfo="{
                title: totalDisplayedPosts[i].title, desc: totalDisplayedPosts[i].description, content: totalDisplayedPosts[i].content
                , image: totalDisplayedPosts[i].urlToImage, link: totalDisplayedPosts[i].url
            }" />
        </div>
        <div v-else>
            <p>Sorry, try another request</p>
        </div>
        <div>
            <paginationPostBoard :total=totalposts :item=amount @pageChanged="changePage" :updatePage=page />
        </div>
    </div>
</template>
<script>
import newsPost from './News_Post.vue';
import paginationPostBoard from "./Pagination.vue"
export default {
    name: 'postPanel',
    props: {
        newQuerry: {
            type: String,
            required: true,
            default: () => {
                return "Apple"
            }
        },
        amount: {
            default() {
                return 6;
            }
        }
    },
    data() {
        return {
            posts: null,
            selectedPost: null,
            page: 1,
            totalposts: 10,
            itemsOnPage: 6,
        }
    },
    components: {
        newsPost,
        paginationPostBoard
    },
    watch: {
        newQuerry: 'fetchData',
        amount: 'changeTotalPostsOnPage',

    },
    methods: {
        fetchData() {
            let querry = 'q=' + this.newQuerry + "&";
            var url = 'https://newsapi.org/v2/everything?' +
                querry +
                'from=2023-08-27&' +
                'sortBy=popularity&' +
                'apiKey=b31fcdc8b21948dab1c86180ea11f5fb';

            var req = new Request(url);

            fetch(req)
                .then((response) => {
                    return response.json();
                })
                .then((data) => {
                    this.posts = data;
                    JSON.stringify(this.posts);
                    this.totalposts = this.posts.articles.length;
                    this.updatePage();
                })
                .catch((error) => {
                    console.log('Помилка: ' + error);
                });
        },
        changeTotalPostsOnPage(amount) {
            this.itemsOnPage = amount;
        },
        changePage(data) {
            this.page = data;
        },
        updatePage() {
            this.page = 1;
        }
    },
    computed: {
        totalDisplayedPosts() {
            let pages = [];
            for (let i = 1; i <= (this.totalposts / this.itemsOnPage); i++) {
                const startIndex = (this.page - 1) * this.itemsOnPage;
                const endIndex = startIndex + this.itemsOnPage;
                pages.push(this.posts.articles.slice(startIndex, endIndex));
            }
            return pages[this.page - 1];
        },
    },
    mounted() {
        this.fetchData();
    }
}
</script>

<style>
.post-board {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
}
</style>