<template>
  <div class="container">
    <Sidebar :temp="weather.list">
      <template #content>
        <div class="content">

          <div class="days">
            <div class="day">
              <p>Tomorrow</p>
              <img v-if="weather?.list[1]?.weather[0].main == 'Clear'" src="../../public/pic/Clear.png" alt="">
              <img v-else-if="weather?.list[1]?.weather[0].main == 'Snow'" src="../../public/pic/Snow.png" alt="">
              <img v-else="weather?.list[1]?.weather[0].main == 'Rain'" src="../../public/pic/HeavyRain.png" alt="">
              <div class="temperature">
                <p>{{parseInt(weather?.list[1]?.main.temp - 273)}} <sub> <sup>o</sup>c</sub></p>
                <p>{{weather?.list[1]?.weather[0].main}}</p>
              </div>
            </div>
            <div class="day">
              <p>{{dayjs().add(2, 'days').format('D, MMM YYYY')}}</p>
              <img v-if="weather?.list[2]?.weather[0].main == 'Clear'" src="../../public/pic/Clear.png" alt="">
              <img v-else-if="weather?.list[2]?.weather[0].main == 'Snow'" src="../../public/pic/Snow.png" alt="">
              <img v-else="weather?.list[2]?.weather[0].main == 'Rain'" src="../../public/pic/HeavyRain.png" alt="">
              <div class="temperature">
                <p>{{parseInt(weather?.list[2]?.main.temp - 273)}} <sub> <sup>o</sup>c</sub></p>
                <p>{{weather?.list[2]?.weather[0].main}}</p>
              </div>
            </div>
            <div class="day">
              <p>{{dayjs().add(3, 'days').format('D, MMM YYYY')}}</p>
              <img v-if="weather?.list[3]?.weather[0].main == 'Clear'" src="../../public/pic/Clear.png" alt="">
              <img v-else-if="weather?.list[3]?.weather[0].main == 'Snow'" src="../../public/pic/Snow.png" alt="">
              <img v-else="weather?.list[3]?.weather[0].main == 'Rain'" src="../../public/pic/HeavyRain.png" alt="">
              <div class="temperature">
                <p>{{parseInt(weather?.list[3]?.main.temp - 273)}} <sub> <sup>o</sup>c</sub></p>
                <p>{{weather?.list[3]?.weather[0].main}}</p>
              </div>
            </div>
            <div class="day">
              <p>{{dayjs().add(4, 'days').format('D, MMM YYYY')}}</p>
              <img v-if="weather?.list[4]?.weather[0].main == 'Clear'" src="../../public/pic/Clear.png" alt="">
              <img v-else-if="weather?.list[4]?.weather[0].main == 'Snow'" src="../../public/pic/Snow.png" alt="">
              <img v-else="weather?.list[4]?.weather[0].main == 'Rain'" src="../../public/pic/HeavyRain.png" alt="">
              <div class="temperature">
                <p>{{parseInt(weather?.list[4]?.main.temp - 273)}} <sub> <sup>o</sup>c</sub></p>
                <p>{{weather?.list[4]?.weather[0].main}}</p>
              </div>
            </div>
            <div class="day">
              <p>{{dayjs().add(5, 'days').format('D, MMM YYYY')}}</p>
              <img v-if="weather?.list[5]?.weather[0].main == 'Clear'" src="../../public/pic/Clear.png" alt="">
              <img v-else-if="weather?.list[5]?.weather[0].main == 'Snow'" src="../../public/pic/Snow.png" alt="">
              <img v-else="weather?.list[5]?.weather[0].main == 'Rain'" src="../../public/pic/HeavyRain.png" alt="">
              <div class="temperature">
                <p>{{parseInt(weather?.list[5]?.main.temp - 273)}} <sub> <sup>o</sup>c</sub></p>
                <p>{{weather?.list[5]?.weather[0].main}}</p>
              </div>
            </div>
          </div>
          <div class="head">
            <h2>Today,s Hightlights</h2>
          </div>
          <div class="boxes">
            <div class="box">
              <p>Wind Status</p>
              <h1>7mph</h1>
            </div>
            <div class="box">
              <p>Humidity</p>
              <h1>84%</h1>
              <span style="width: 50%" data-progress="100%"></span>
            </div>
            <div class="box">
              <p>Visibility</p>
              <h1>6,4 milis</h1>
            </div>
            <div class="box">
              <p>Air Pressure</p>
              <h1>998mb</h1>
            </div>
          </div>
        </div>
      </template>
    </Sidebar>
  </div>

</template>
<script async setup>
import Sidebar from '../components/Sidebar.vue';
import axios from "axios";
import dayjs from "dayjs"
import { onMounted, ref } from 'vue';

const ip = ref("");
const location = ref([]);
const weather = ref([]);
const ipAddress = await axios.get("https://api.ipify.org/?format=json");
ip.value = ipAddress.data.ip
const locationData = await axios.get(`https://geo.ipify.org/api/v2/country,city,vpn?apiKey=at_ncF5xe0nsomy384wA5xJnb6LzWLxL&ipAddress=` + ip.value);
location.value = locationData.data
const weatherData = await axios.get(`https://api.openweathermap.org/data/2.5/forecast?cnt=6&lat=${location.value.location.lat}&lon=${location.value.location.lng}&appid=3ddc853961f70606c870a3af222a22f7`)
weather.value = weatherData.data


</script>
