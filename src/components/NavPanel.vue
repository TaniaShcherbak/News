<template>
    <div>
        <label for="#amountItems">Posts per page</label>
        <select name="amountItems" id="amountItems" ref="amountSelect" @change="changeAmountItems">
            <option value="6">6</option>
            <option value="12">12</option>
            <option value="24">24</option>
            <option value="48">48</option>
        </select>
    </div>
</template>
<script>
export default {
    name: "navPanel",
    methods: {
        changeAmountItems() {
            let amount = parseInt(this.$refs.amountSelect.value);
            this.$emit('amountItemsOnPage', amount)
        }
    }
}
</script>
<style>
label {
    color: white;
    margin-left: 200px;
    margin-right: 10px;
}
</style>