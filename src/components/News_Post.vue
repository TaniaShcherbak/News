<template>
    <div class="post">
        <a :href='postinfo.link' target="_blank">
            <h2>{{ postinfo.title }}</h2>
            <p>{{ postinfo.author }}</p>
            <img :src='postinfo.image' alt="image">
            <p>{{ postinfo.desc }}</p>
        </a>
    </div>
</template>
<script>
export default {
    name: 'newsPost',
    props: {
        postinfo: {
            type: Object,
        }
    }

}
</script>
<style>
.post {
    width: 25vw;
    padding: 20px;
    text-align: center;
    cursor: pointer;
    background-color: rgb(240, 235, 235);
    border-radius: 3%;
    margin: 20px;
    box-shadow: 5px 5px 10px #f5f3f3;
    transition: background-color 0.3s, box-shadow 0.3s;
    font-size: 28px;
    transition: transform 0.3s;
}

.post:hover {
    transform: scale(1.05);
}

img {
    width: 80%;
}

a {
    text-decoration: none;
    color: black;
}

.post:hover {
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.post h2 {
    transition: color 0.3s;
    font-size: 32px;
}

.post:hover h2 {
    color: brown;
}
</style>
