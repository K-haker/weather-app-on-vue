<template>
    <div class="days">

<!--    <div  class="day" v-for="(day, index) in dataSixDays" :key="index"> 
            <h3 class="day-name"><span class="day-number">{{new Date(day.dt * 1000).getDate()}}</span>.<span class="months-numder">{{(new Date(day.dt * 1000).getMonth())+ 1}}</span></h3>
            <div class="day-weather">
                <img class="day-weather__img" alt="">
            </div>
            <div class="day-temperature"> <span class="day-temp">{{Math.round(day.temp.day)}}</span>&#176; </div>
            <div class="day-weather__word">{{day.weather[0].description}}</div>
        </div>
    -->

        <div  class="day" v-for="i in 6"  :key="i*4">
            <h3 class="day-name"><span class="day-number">{{new Date(dataSixDays[i].dt * 1000).getDate()}}</span>.<span class="months-numder">{{(new Date(dataSixDays[i].dt * 1000).getMonth())+ 1}}</span></h3>
            <div class="day-weather">
                <img class="day-weather__img" alt="">
            </div>
            <div class="day-temperature"> <span class="day-temp">{{Math.round(dataSixDays[i].temp.day)}}</span>&#176; </div>
            <div class="day-weather__word">{{dataSixDays[i].weather[0].description}}</div>
        </div>



    </div>

</template>
  
<script>
import axios from "axios"

export default {
    name: 'OneDay',


    data(){
        return{
            dataSixDays:[

            ]
        }
    },

    methods:{
        async weatherFetch(){
            try{
                const response = await axios.get(`https://api.openweathermap.org/data/2.5/onecall?lat=58.0105&lon=56.2502&units=metric&exclude=minutely,hourly&lang=RU&appid=7590b58fc327c0300af42791a4390329`)
                this.dataSixDays = response.data.daily
                console.log(response)
            } catch(e){
                alert("Ошибка!")
            }
        },
    },

    beforeMount(){
        this.weatherFetch()
    }

}
</script>

<style scoped>
.days{
   display: -webkit-box;
   display: -ms-flexbox;
   display: flex;
   -webkit-box-pack: justify;
   -ms-flex-pack: justify;
   justify-content: space-between;
   margin: 30px;
}

.day{
    text-align:center;
    color: #434343;
    width: 100%;
    max-width: 150px;
    }

    .day-name{
    margin-bottom: 30px;
    }

    .day-temperature{
    font-size: 20px;
    margin-bottom: 15px;
    }

    .day-weather__word{
    font-size: 14px;
    }
</style>