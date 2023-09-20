<template>
    <div>
        <label for="#amountItems">Number of elements per page</label>
        <select name="amountItems" id="amountItems" ref="amountSelect" @change="changeAmountItems">
            <option value="8">8</option>
            <option value="16">16</option>
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