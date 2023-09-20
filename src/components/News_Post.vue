<template>
    <div class="post">
        <!-- выводим значения принятого объекта -->
        <h2>{{ postinfo.title }}</h2>
        <p>{{ postinfo.author }}</p>
        <p>{{ postinfo.desc }}</p>
        <img @click="show" :src='postinfo.image' alt="image">
    </div>
</template>
<script>
export default {
    name: 'newsPost',
    props: {
        postinfo: {//принимаем из родительского
            type: Object,
        }
    },
    methods:{
        show(){
            console.log(this.postinfo);
        }
    }

}
</script>
<style>
.post {
    display: block;
    width: 25vw;
    padding: 20px;
    text-align: center;
    cursor: pointer;
    border: 2px solid black;
    margin-bottom: 50px;
}

img {
    width: 200px;    
}
</style>