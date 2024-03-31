<!-- <template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->


<template>
    <div>
      Current Temperature in Belleville, Ontario: {{ temperature }}°C
    </div>
</template>
  
<script setup>
    import { ref, watchEffect } from 'vue'
    import axios from 'axios'
    
    const API_KEY = '16a7c8df51f41fbc79eaf3d33cadf98f'
    const API_URL = 'https://api.openweathermap.org/data/2.5/weather?q=Belleville,CA&units=metric&appid=16a7c8df51f41fbc79eaf3d33cadf98f'
    
    const temperature = ref(null)
    const error = ref(null)
    
    watchEffect(async () => {
        try {
            const response = await axios.get(API_URL, {
                params: {
                    appid: API_KEY
                }
            })
            temperature.value = response.data.main.temp
            error.value = null
        } catch(error) {
            console.error('Temperature could not be fetched:', error)
            temperature.value = null
            error.value = 'Data was not able to be fetched through Axios'
        }
    })
</script>
  
<style>
  /* Your CSS styles here */
</style>