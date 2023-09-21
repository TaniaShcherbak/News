<template>
    <div class="pagination">
        <ul>
            <li v-for="page in totalPages" :key="page">
                <button @click="changePage(page)" class="pagination-button" :class="{ active: currentPage === page }">{{
                    page
                }}</button>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    name: "paginationPostBoard",
    props: {
        total: {
            type: Number,
            default() {
                return 1;
            }
        },
        item: {
            type: Number,
            default() {
                return 8
            }
        },
        updatePage: {
            type: Number
        }
    },
    data() {
        return {
            currentPage: 1
        }
    },
    watch: {
        updatePage: 'UpdatePagination'
    },
    computed: {
        totalPages() {
            return Math.ceil(this.total / this.item);
        }
    },
    methods: {
        changePage(pageNumber) {
            this.currentPage = pageNumber;
            this.$emit('pageChanged', pageNumber)
        },
        UpdatePagination(data) {
            this.currentPage = data;
        }
    }
}
</script>
<style>
ul {
    display: flex;
    flex-direction: row;

}

.pagination {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 50px;
    margin-top: 20px;
}

ul li {
    list-style-type: none;
    margin: 3px;
}
ul li button {
    border: none;
    background: transparent;
    color: white;
    font-size: 18px;

}
ul li button:hover{
    scale: 1.5;
}

.active {
    color: brown;
}
</style>