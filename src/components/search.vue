<template>
    <div class="search">
        <input class="input"
            type="text"
            placeholder="search"
            name="search"
            id="searchInput"
            @keyup.enter="getrequest"
        />
        <img  @click="getrequest" class="searchImage" src="../../public/search.png" alt="search">
    </div>
</template>
<script>
export default {
    name: "searchBar",
    methods: {
        getrequest() {
            let search = document.getElementById("searchInput").value;
            this.$emit("searchQuerry", search);
            document.getElementById("searchInput").value = "";
        },
    },
};
</script>

<style>
.search{
    display: flex;
    flex-direction: row;
    background-color: rgb(250, 248, 248);
    align-self: center;
    height: 50px;
    border-radius:25px;
    width: 250px;
    border:none;
    background-color: rgb(245, 244, 244);
    margin-top: 30px;
    padding-left: 10px;
    opacity: 80%;

}
.searchImage{
    width: 50px;
    height: 50px;
    cursor: pointer;
}
div input {
    padding: 0;
    border-radius: 25px;
    border: none;
    width: 250px;
    outline: none;
     opacity: 100%;
}
input::placeholder {
    padding-left: 5px;
}
</style>
