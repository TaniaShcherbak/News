<template>
    <div class="panel">
        <div v-if="posts" class="post-board">
            <newsPost v-for="(index, i) in 10" :key="i" :postinfo="{ //передаем его в дочерн эл-т
                title: posts.articles[i].title, desc: posts.articles[i].description, content: posts.articles[i].content
                , image: posts.articles[i].urlToImage
            }" />
        </div>
        <div v-else>
            <p>Sorry, try another request</p>
        </div>
    </div>
</template>
<script>
import newsPost from './News_Post.vue';
export default {
    name: 'postPanel',
    props: {
        newQuerry: {
            type: String,
            required: true,
            default: () => {
                return "Apple"
            }
        }
    },
    data() {
        return {
            posts: null,
            selectedPost: null,
        }
    },
    components: {
        newsPost,
    },
    watch: {
        newQuerry: 'fetchData'
    },
    methods: {
        fetchData() {
            let querry = 'q=' + this.newQuerry +"&";
            // var url = 'https://newsapi.org/v2/everything?' +
            //     querry +
            //     'from=2023-08-19&' +
            //     'sortBy=popularity&' +
            //     'apiKey=b31fcdc8b21948dab1c86180ea11f5fb';
            var url = 'https://newsapi.org/v2/everything?' +
                querry +
                'from=2023-08-20&' +
                'sortBy=popularity&' +
                'apiKey=a053a630c58d46509b7fe99976290f7f';
            var req = new Request(url);

            fetch(req)
                .then((response) => {
                    return response.json();
                })
                .then((data) => {
                    this.posts = data;
                    JSON.stringify(this.posts);
                })
                .catch((error) => {
                    console.log('Помилка: ' + error);
                });
        }
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