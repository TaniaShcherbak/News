<template>
    <div class="post">
        <a :href='postinfo.link' target="_blank">
            <div class="header-post">
                <h2>{{ postinfo.title }}</h2>
            </div>
            <div class="body-post">
                <p>{{ postinfo.author }}</p>
                <img :src='postinfo.image' alt="image">
                <p>{{ postinfo.desc }}</p>
            </div>
        </a>
        <div @click="toggleHeart" class="like">
            <i class="fas fa-heart" :class="{ 'liked': liked }"></i>
            {{ counter }}
        </div>
    </div>
</template>
<script>
export default {
    name: 'newsPost',
    props: {
        postinfo: {
            type: Object,
        }
    },
    data() {
        return {
            counter: Math.floor(Math.random() * 10000) + 1,
            clicked: false,
            liked: false,
        };
    },
    methods: {
        toggleHeart() {
            this.liked = !this.liked;
            if (this.liked) {
                this.counter++;
            } else {
                this.counter--;
            }
        },
    },
};
</script>
<style scoped>
.post {
    width: 25vw;
    text-align: center;
    cursor: pointer;
    background-color: rgb(240, 235, 235);
    border-radius: 3%;
    margin: 30px;
    box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
    transition: background-color 0.3s, box-shadow 0.3s;
    font-size: 18px;
    transition: transform 0.3s;
    overflow: hidden;
    position: relative;
    font-family: 'Roboto', sans-serif;
}

img {
    width: 90%;
}

a {
    text-decoration: none;
    color: black;
}

.post:hover {
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.header-post {
    background-color: brown;
    color: white;
    padding: 0;
    overflow: hidden;
}

.body-post {
    padding: 20px;
}

.body-post:hover {
    color: rgb(16, 16, 115);
}

.post h2 {
    transition: color 0.3s;
    font-size: 24px;
    padding: 20px;
    margin: 0;
}

.like {
    position: absolute;
    right: 30px;
    bottom: 20px;
}

.fa-heart:hover {
    transform: scale(1.1);
    color: brown;
}

.liked {
    color: brown;
}</style>
