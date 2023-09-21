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
    margin-left: 120px;
    margin-right: 10px;
    font-size: 22px;

}

div select {
    font-size: 16px;
    border-radius: 10px;
    background-color: rgb(245, 244, 244);
    border: none;
    cursor: pointer;
}

#amountItems option {
    cursor: pointer;
}
</style>