<template>
  <div class="weather-top">
    <div class="present-data">
        <div class="present-temperature"><span id="temperature-now"> {{(Math.round(dataToday.main.temp - 273.15)) }}</span>&#176;</div>
        <div id="current-clarity" class="present-clarity">{{ dataToday.weather[0].description }}</div>
    </div>
    <div class="city">
        <div class="city-name">Пермь</div>
    </div>
  </div>
</template>
  
<script>
import axios from "axios"

export default {
  name: 'OneDay',
  data(){
    return{
      dataToday:{
        main: "",
        weather:[{
          0:"description"
        }]
      },
    }
  },

  methods:{
    async weatherFetch(){
        const response = await axios.get(`http://api.openweathermap.org/data/2.5/weather?q=Perm&lang=RU&appid=7590b58fc327c0300af42791a4390329`)
        this.dataToday = response.data
    }
  },

  
  beforeMount(){
    this.weatherFetch()
 }
}
</script>

<style>
  .weather-top{
    height: 200px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    padding: 70px 100px  0px;
    background-image: url("../assets/weather-app-js.jpg");
    background-size: cover;
  }

  .present-data{
    text-align: center;
  }

  .present-temperature{
    font-size: 70px;
    color: rgb(255, 255, 255);
  }

  .present-clarity{
    color: rgba(255, 255, 255, 1.0);
    text-transform: uppercase;
  }

  .city-name{
    color: rgb(255,255,255);
    font-size: 25px;
    text-transform: uppercase;
  }

  .today-block{
   width: 100%;
   display: -webkit-box;
   display: -ms-flexbox;
   display: flex;
   -webkit-box-align: center;
   -ms-flex-align: center;
   align-items: center;
   -webkit-box-pack: justify;
   -ms-flex-pack: justify;
   justify-content: space-between;
   margin-bottom: 10px;
}

.today-weather{
   display: -webkit-box;
   display: -ms-flexbox;
   display: flex;
   -webkit-box-align: center;
   -ms-flex-align: center;
   align-items: center;
}

.today-weather-img{
   margin-right: 10px;
}

</style>