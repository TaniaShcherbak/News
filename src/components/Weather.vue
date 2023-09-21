<template>
    <div v-if="weather" class="weather">
        <div>
            <p>{{ weather.location.name }} {{ weather.location.country }}</p>
            <p>{{ weather.location.localtime }}</p>
            <p>{{ weather.current.temp_c }} &#8451;</p>
            <input type="text" placeholder="type in city" name="searchWeather" id="searchWeather" @keyup.enter="getrequest">
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
            icon: null,
            city: 'Vinnitsa'
        }
    },
    methods: {
        getrequest() {
            let search = document.getElementById("searchWeather").value;
            this.city = search;
            this.fetchWeather();
            document.getElementById("searchWeather").value = "";
        },
        fetchWeather() {
            const url = 'https://weatherapi-com.p.rapidapi.com/forecast.json?q=' + this.city + '&days=3';
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
                    this.icon = "https:" + this.weather.current.condition.icon;
                })
                .catch((error) => {
                    console.log('Помилка: ' + error);
                });
        }
    },
    mounted() {
        this.fetchWeather();
    }
}
</script>
<style>
.weather {
    min-width: 400px;
    background-color: #15222c;
    color: white;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    border-radius: 15px;
    padding: 20px;
}

.weather img {
    width: 100px;
}

.weather input {
    height: 30px;
    padding-left: 10px;
}

.weather input::placeholder {
    padding-left: 5px;
}
</style>