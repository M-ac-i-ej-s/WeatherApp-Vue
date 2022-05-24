<template>
<div class="container">
    <div id="Wind">
       <p><i class="fa-solid fa-wind"></i></p>
       <p style="margin-top:12px">{{windSpeed}} km/h</p>
       <p>{{direction(windDir)}}</p>
    </div>
    <div id="clouds">
       <p><i class="fa-solid fa-cloud"></i></p>
       <p style="margin-top:15px;font-size:30px">{{cloudsPer}}%</p>
    </div>
    <div id="SunRiseSet">
       <p><i class="fa-solid fa-sun"></i><i class="fa-solid fa-arrow-up-long"></i></p>
       <p><i class="fa-solid fa-sun"></i><i class="fa-solid fa-arrow-down-long"></i></p>
       <p style="margin-top:20px">{{convertHMS(sunRise)}}</p>
       <p style="margin-top:20px">{{convertHMS(sunSet)}}</p>
    </div>
</div>   
</template>

<script>
export default {
    name: 'Under',
    props: {
      windSpeed: Number,
      windDir: Number,
      cloudsPer: Number,
      sunRise: String,
      sunSet: String
    },
    methods: {
      convertHMS(value) {
      var date = new Date(value * 1000);
      return date.toLocaleTimeString();
      },
      direction(value) {
        if(0<=value<45 || 315<value<360) return "North"
        if(45<=value<135) return "West"
        if(135<=value<225) return "South"
        if(225<=value<315) return "East"
      }
    }
}
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 150px 150px;
  grid-gap: 25px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  margin-top: 140px;
  /* margin-left: 140px; */
  text-align: center;
  color: white;
}
.container > div { 
  background-color: rgba(218, 214, 214, 0.5);
  height: 130px;
  border-radius: 25px;
}
#SunRiseSet {
  grid-column:1/3;
  display: grid;
  grid-template-columns: 100px 100px;
  grid-template-rows: 50px 50px;
  font-size: 25px;
  justify-content: space-around;
}
i {
  margin-left: 10px;
  margin-right: 10px;
  margin-top: 15px;
  font-size: 35px;
}
</style>