<template>
    <div v-if="currency" class="main converter">
        <div>
            <p class="title">Exchahge rate</p>
            <table>
                <thead>
                    <tr>
                        <th>Currency</th>
                        <th>Buy</th>
                        <th>Cell</th>
                    </tr>
                </thead>
                <tbody v-for="(index, i) in 2" :key="i">
                    <tr>
                        <td>{{ currency[i].currencyCodeA == 840 ? "USD" : "EUR" }}</td>
                        <td>{{ currency[i].rateBuy }}</td>
                        <td>{{ currency[i].rateSell }}</td>
                    </tr>
                </tbody>
                <tr>
                    <td>RUS</td>
                    <td style=" text-align:center; background-color: white;"><img src="@/assets/died.png" alt=""
                            style="width: 25px;"></td>
                    <td style=" text-align:center; background-color: white;"><img src="@/assets/died.png" alt=""
                            style="width: 25px;"></td>
                </tr>

            </table>
        </div>
    </div>
</template>
<script>
export default {
    name: 'currencyConvert',
    data() {
        return {
            currency: null,
        }
    },
    mounted() {
        var url = 'https://api.monobank.ua/bank/currency'
        var req = new Request(url);
        fetch(req)
            .then((response) => {
                return response.json();
            })
            .then((data) => {
                this.currency = data;
                JSON.stringify(this.currency);
            })
            .catch((error) => {
                console.log('Помилка: ' + error);
            });
    }
}
</script>
<style>
.converter {
    color: white;
    background-color: rgba(21, 34, 44, 0.7);

    border-radius: 15px;
    width: 300px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-bottom: 40px;
}

.converter .title {
    text-align: center;
    font-size: 20px;
}

.converter table {
    margin: 0 auto;
}

table {
    border-collapse: collapse;
}

table,
th,
td {
    font-size: 20px;
    padding: 8px;
    border: 2px solid darkgrey;
}</style>