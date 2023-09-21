<template>
    <div v-if="weather" class="weather">
        <div>
            <p>{{ weather.location.name }} {{ weather.location.country }}</p>
            <p>{{ weather.location.localtime }}</p>
            <p>{{ weather.current.temp_c }} &#8451;</p>
        </div>
        <div>
            <img :src="icon" alt="day/night">
        </div>

    </div>
</template>
<script>
export default {
    name: "weatherPanel",
    data() {
        return {
            weather: null,
            icon: null
        }
    },
    mounted() {
        const url = 'https://weatherapi-com.p.rapidapi.com/forecast.json?q=Vinnitsa&days=3';
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': '63832d5d1fmshab60483220d5186p143190jsnbc1bac78b8e2',
                'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
            }
        };
        fetch(url, options)
            .then((response) => {
                return response.json();
            })
            .then((data) => {
                this.weather = data;
                JSON.stringify(this.weather);
                this.icon="https:" + this.weather.current.condition.icon;
                console.log(this.icon)
            })
            .catch((error) => {
                console.log('Помилка: ' + error);
            });
        // try {
        //     const response = fetch(url, options);
        //     const result = response.text();
        //     console.log(result);
        // } catch (error) {
        //     console.error(error);
        // }
    }
}
</script>
<style>
.weather {
    width: 300px;
    background-color: #15222c;
    color: white;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    border-radius: 15px;
}
.weather img {
width: 100px;
}
</style>