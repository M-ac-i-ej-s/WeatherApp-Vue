<template>
  <p id="celcius">{{Celcius}}</p>
  <p :style="{display: visible}" id="symbol">°</p>
  <p id="place">{{Place}}</p>
</template>

<script>
export default {
  name: 'Front',
  props: {
    Celcius: String,
    Place: String,
    visible: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
p{
  color: rgb(230, 230, 230);
  position: absolute;
}
#celcius {
  margin-left: auto;
  margin-right: auto;
  font-size: 120px;
  margin-top: 150px;
  left: 0;
  right: 0;
  text-align: center;
}
#symbol {
  position: absolute;
  left: 50%;
  top: 250px;
  transform: translate(-50%, -50%);
  text-align: center;
  font-size: 70px;
  margin-left: 50px;
}
#place {
  margin-left: auto;
  margin-right: auto;
  font-size: 40px;
  margin-top: 300px;
  left: 0;
  right: 0;
  text-align: center;
}

</style>
