<template>
    <div class="post">
        <a :href='postinfo.link' target="_blank">
            <h2>{{ postinfo.title }}</h2>
            <p>{{ postinfo.author }}</p>
            <p>{{ postinfo.desc }}</p>
            <img :src='postinfo.image' alt="image">
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
}

img {
    width: 200px;
}
a {
    text-decoration: none;
    color: black;
}
</style>