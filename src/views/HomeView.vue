<template>
  <div>
    <h1 class="title">{{ nome }} </h1>
  
    <ul class="row">
      <li class="col-m header" style="text-align: start;">Clube:</li>
      <li class="col-l header">Pts:</li>
      <li class="col-l header">PJ:</li>
      <li class="col-l header">VIT:</li>
      <li class="col-l header">E:</li>
      <li class="col-l header">DER:</li>
      <li class="col-l header">GM:</li>
      <li class="col-l header">GS:</li>
      <li class="col-l header">SG:</li>
    </ul>
  
    <div v-for="time in times" :key="time.id">
      <row :time="time"></row>
    </div>
  </div>
  
  <div class="geral" style="background-color: #f8f9fa;">
    <div class="cor">
      <div class="Quadrado" style="background-color:#4285F4;"></div>
      <div class="text">Fase de grupos da Copa Libertadores</div>
    </div>
  
    <div class="cor">
      <div class="Quadrado" style="background-color:#FA7B17;"></div>
      <div class="text">Qualificatórias da Copa Libertadores</div>
    </div>
  
    <div class="cor">
      <div class="Quadrado" style="background-color:#34A853;"></div>
      <div class="text">Fase de Grupos da Copa Sul-Americana</div>
    </div>
  
    <div class="cor">
      <div class="Quadrado" style="background-color:#EA4335;"></div>
      <div class="text">Rebaixamento</div>
    </div>
  </div>
</template>

<script>
import Row from '../components/Row.vue'
const API_URL = `https://api-football-standings.azharimm.dev/leagues/bra.1/standings?season=2024&sort=asc`

export default {
  data: () => ({
    nome: '',
    times: []
  }),
  methods: {
    async getTimes() {
      const response = await fetch(API_URL)
      const data = await response.json()

      //console.log(data.data.standings)

      this.nome = data.data.name
      this.times = data.data.standings

    },
    
  },
  created() {
    this.getTimes()
  },
  components:{
    Row
  },
}
</script>

<style>
body {
  background-color: rgb(255, 253, 253);
}

.title {
  color: #FFE807;
  text-align: center;
}
.row {
  text-align: start;
  align-content: center;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  margin: 0;
}

.header {
  color: #FFE807;
  font-weight: bold;
  font-size: 14px;
  background-color: #121212 !important;
  text-align: center;
}

.row li {
  background-color: white;
  display: inline-block;
  padding: 10px;
  border: 1px solid black;
  text-align: center;
}

.col-l {
  width: 35px;
}

.col-m {
  width: 230px;
}

.col-g {
  width: 250px;
}
#app{
  margin-left: 70px;
  margin-right: 70px;
}

.cor {
  align-items: center;
  display: flex;
  margin-bottom: 2px;
  margin-top: 2px;
}
.Quadrado {
border-radius: 1px;
display: inline-block;
height: 8px;
vertical-align: middle;
width: 8px;
}
.text{
margin-left: 10px;
}
.geral{
background-color: #f8f9fa;
padding: 6px 8px 10px;
border-radius: 4px;
border: 1px solid var(--gS5jXb);
margin: 8px;
font-size: 12px;
line-height: 16px;
}

</style>