<template>
    <div class="sidebar">
        <button @click="toggle" :style="{display: toggleStatus == true ? 'none' : ''}">Search for place</button>
        <input type="text" placeholder="Search for place"
            :style="{display: toggleStatus == true ? 'block' : 'none', width: '100%',padding: '5px',border: 'none',outline: 'none'}" />
        <div class="weather-img">
            <img class="background" src="../../public/pic/Cloud-background.png">
            <img class="weather" src="../../public/pic/Shower.png" alt="">
        </div>
        <h1>{{parseInt(temp[0]?.main?.temp - 273)}} <sub> <sup>o</sup>c </sub></h1>
        <h2>{{temp[0]?.weather[0]?.main}}</h2>
        <div class="day">
            <p>today . fri 5 jun</p>
        </div>
    </div>
    <slot name="content"></slot>
</template>
<script setup>
import { ref } from 'vue';

const props = defineProps(['temp'])
const toggleStatus = ref(false);
const toggle = () => {
    toggleStatus.value = !toggleStatus.value
}
</script>
