<template>
<div id="app" class="contenido">
  <h1 class="contador">{{contadorMin < 10 ? '0'+contadorMin : contadorMin }}:{{contadorSeg < 10 ? '0'+contadorSeg : contadorSeg }} min/seg</h1>
  <div class="botones">
    <button class="btn" style="cursor:pointer;" @click="iniciar(5)">5 segs</button>
    <button class="btn" style="cursor:pointer;" @click="iniciar(10)">10 min</button>
    <button class="btn" style="cursor:pointer;" @click="iniciar(30)">30 min</button>
    <button class="btn" style="cursor:pointer;" @click="iniciar(60)">60 min</button>
  </div>
</div>
</template>

<script>
export default {
  name: "Barto",
  data() {
    return {
      contadorMin: 0,
      contadorSeg: 0,
      myIntervalo: null,
    };
  },
  methods: {
    iniciar(time) {
      this.contadorSeg = time;
      clearInterval(this.myIntervalo);
      this.myIntervalo = setInterval(() => {
        this.contadorSeg > 0 ? this.contadorSeg-- : false;
      }, 1000);
      setTimeout(() => {
        clearInterval(this.myIntervalo);
      }, (time + 1) * 1000);
    },
  },
};
</script>

<style lang="scss">
#app {
  max-width: 400px;
  margin: auto;
  padding: 20px 0;
  background-color: rgba(46, 46, 48, 0.082);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  ul {
    li {
      color: rgb(73, 130, 214);
    }
  }
}
.contador {
  color: rgba(102, 101, 101, 0.61);
}
.btn {
  color: rgb(245, 245, 245);
  background-color: rgba(62, 121, 230, 0.897) ;
  border-style: hidden;
  border-radius: 5px;
  padding: 10px 10px;
  margin: 0 5px;
}
</style>