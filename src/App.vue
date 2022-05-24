<template>
<div class="main">
  <img src="./assets/frontPage.jpg" alt="Background">
  <Header @input="onSelectedChild"></Header>
  <Front :visible="celciusValue!==nothing ? 'block' : 'none'"  :Celcius="celciusValue" :Place="placeValue"/>
  <Under :windDir="windDirValue" :windSpeed="windSpeedValue" :cloudsPer="cloudsPerValue" :sunRise="sunRiseValue" :sunSet="sunSetValue"></Under>
</div>
</template>

<script>
import Front from './components/Front.vue'
import Header from './components/Header.vue'
import Under from './components/Under.vue'

export default {

  name: 'App',
  components: {
    Front,
    Header,
    Under
  },
  data() {
    return {
      celciusValue: "0",
      placeValue: "City",
      windDirValue: "", 
      windSpeedValue: "",
      cloudsPerValue: "",
      sunRiseValue: "",
      sunSetValue: "",
      nothingValue: ""
    }
  },
  methods: {
    async onSelectedChild(value) {
      fetch(`http://api.openweathermap.org/data/2.5/weather?q=${value}&appid=1ad92159eb08e9212c1e2b681ff4f804`)
      .then(res => res.json())
      .then(data => {
        this.celciusValue = Math.round(data['main']['temp']-273)
        this.placeValue = data['name']
        this.windDirValue = data['wind']['deg']
        this.windSpeedValue = data['wind']['speed']
        this.cloudsPerValue = data['clouds']['all']
        this.sunRiseValue = data['sys']['sunrise']
        this.sunSetValue = data['sys']['sunset']
      })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
  text-align: center;
  margin-top: 60px;
}
img {
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  left: 0;
  right: 0;
  text-align: center;
  width: 400px;
  border: 2px solid #2c3e50;
  border-radius: 20px;
}
</style>
