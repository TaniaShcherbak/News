<template>
    <div>
        <input type="text" name="search" id="searchInput">
        <button @click="getrequest">Search</button>
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