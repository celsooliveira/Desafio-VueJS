<template>
  <div id="app">
    <Painel msg="Programado para ganhar a partir da segunda tentativa, para melhor efeito de testes(Sugestão: Jogar 3 vezes para testar)"/>
  </div>
</template>

<script>
import Painel from './components/Painel.vue'

export default {
  name: 'App',
  components: {
    Painel
  }
}
</script>

<style>
body{
  background-image: linear-gradient(to right,rgb(0, 0, 0), rgb(67, 67, 67));
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 0.8em;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}
</style>
