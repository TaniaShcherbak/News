<template>
    <div>
        <h2>{{ post.title }}</h2>
        <div>{{ post.content }}</div>
        <img :src='post.image' alt="image">
        <p>{{ post.author }}</p>
    </div>
</template>
<script>
export default {
    name: "detailPost",
    props: {
        post: {
            type: Object,
        }

    }
}
</script>