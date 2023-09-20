<template>
    <div class="search">
        <input type="text" name="search" id="searchInput" @keyup.enter="getrequest">
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
    width: 250px;
    height: 30px;
    margin-bottom: 30px;
}

</style>