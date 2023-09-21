<template>
    <div class="search">
        <input
            type="text"
            placeholder="search"
            name="search"
            id="searchInput"
            @keyup.enter="getrequest"
        />
        <i><img src="../assets/search-icon-png-22.png" alt="search"/></i>
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
.search {
    display: flex;
    flex-direction: row;
    border: 1px solid rgb(245, 244, 244);
    background-color: rgb(245, 244, 244);
    border-radius: 10px;
    height: 30px;
    align-items: center;
}
div input {
    padding: 0;
    width: 200px;
    height: 30px;
    border: none;
    height: 30px;
    border-radius:10px;
}
input::placeholder {
    padding-left: 10px;
    
}
img {
    width: 25px;
    height: 25px;
    text-align: center;
    margin-left: -5px;
    padding-right: 5px;
    cursor: pointer;
}
</style>
