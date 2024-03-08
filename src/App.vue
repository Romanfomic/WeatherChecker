<template>
    <div class="wrapper">
        <h1>Погода в Вашем городе</h1>
        <input type="text" v-on:input="city = $event.target.value" placeholder="Введите город...">
        <button v-if="city != ''" v-on:click="getWeather()" >Получить</button>
        <button disabled v-else>Получить</button>
        <p class="error">{{ error }}</p>
        <div v-if="info != null">
            <p>{{showTemp}}</p>
            <p>{{showFeels}}</p>
            <p>{{showMinTemp}}</p>
            <p>{{showMaxTemp}}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            city: "",
            error: "",
            info: null
        }
    },
    methods: {
        getWeather() {
            if (this.city.trim().length < 2) {
                this.error = "Ошибка: короткое название";
                return false;
            }
            this.error = "";

            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=a87622032e1a3efd5f302ae5051a38d0`)
            .then(res => (this.info = res.data));
        }
    },
    computed: {
        showTemp() {
            return "Температура: " + this.info.main.temp + " C";
        },
        showFeels() {
            return "Ощущается, как: " + this.info.main.feels_like + " C";
        },
        showMinTemp() {
            return "Минимальная температура: " + this.info.main.temp_min + " C";
        },
        showMaxTemp() {
            return "Максимальна температура: " + this.info.main.temp_max + " C";
        }

    }
}
</script>

<style>
    .wrapper {
        padding: 200px;
        border-radius: 50px;
        box-shadow: 0 0 2px;
        background-color: white;
    }
    .wrapper h1 {
        margin: 10px 0;
    }
    .wrapper input{
        border: 0;
        background: transparent;
        font-size: 14px;
        border-bottom: 2px solid deepskyblue;
        padding: 5px;
        outline: none;
    }
    .wrapper button {
        border: 0;
        background-color: deepskyblue;
        color: white;
        border-radius: 10px;
        padding: 8px;
        margin: 0 10px;
        transition: transform 0.3s ease;
        cursor: pointer;
    }
    .wrapper button:disabled {
        background-color: white;
        border: 1px solid deepskyblue;
        color: deepskyblue;
        cursor: not-allowed;
    }
    .wrapper button:hover{
        transform: scale(1.1);
    }

    .error {
        margin: 10px 0;
        color: red;
    }
</style>
