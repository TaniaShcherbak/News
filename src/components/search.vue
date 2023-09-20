<template>
    <div class="search">
        <input type="text" placeholder="search" name="search" id="searchInput" @keyup.enter="getrequest">
    </div>
</template>
<script>
export default {
    name: "searchBar",
    methods:
    {
        getrequest() {
            let search = document.getElementById("searchInput").value;
            this.$emit('searchQuerry', search);
            document.getElementById("searchInput").value='';
        }
    }
}
</script>

<style>
div input{
    padding: 0;
    width: 200px;
    height: 30px;
    margin-bottom: 30px;
    border-radius:25px;
    border:none;
    background-color: rgb(245, 244, 244);
    margin-top: 30px;
}
input::placeholder{
    padding-left: 10px;
}

</style>