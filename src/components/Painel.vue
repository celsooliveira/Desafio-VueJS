<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul id="painel">
      <li id="caixa1"> {{premios.premio1}} </li>
      <li id="caixa2"> {{premios.premio2}} </li>
      <li id="caixa3"> {{premios.premio3}} </li>
    </ul>
    <button @click="jogar">JOGAR</button>
    <h3>{{ premios.vencedor }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Painel',
  props: {
    msg: String
  },
  computed: {
    premios () {
      return this.$store.state.premios
    }
  },
  methods: {
    jogar () {
      const intervalPremio1 = setInterval(() => {
        if (this.$store.state.premios.premio1 === '!') {
          this.$store.state.premios.premio1 = '?'
        } else if (this.$store.state.premios.premio1 === '?') {
          this.$store.state.premios.premio1 = '$'
        } else if (this.$store.state.premios.premio1 === '$') {
          this.$store.state.premios.premio1 = '!'
        }
      }, 200)
      const intervalPremio2 = setInterval(() => {
        if (this.$store.state.premios.premio2 === '!') {
          this.$store.state.premios.premio2 = '?'
        } else if (this.$store.state.premios.premio2 === '?') {
          this.$store.state.premios.premio2 = '$'
        } else if (this.$store.state.premios.premio2 === '$') {
          this.$store.state.premios.premio2 = '!'
        }
      }, 100)
      const intervalPremio3 = setInterval(() => {
        if (this.$store.state.premios.premio3 === '!') {
          this.$store.state.premios.premio3 = '?'
        } else if (this.$store.state.premios.premio3 === '?') {
          this.$store.state.premios.premio3 = '$'
        } else if (this.$store.state.premios.premio3 === '$') {
          this.$store.state.premios.premio3 = '!'
        }
      }, 30)
      this.finalizarSorteio(intervalPremio1, intervalPremio2, intervalPremio3)
    },
    finalizarSorteio (intervalPremio1, intervalPremio2, intervalPremio3) {
      setInterval(() => {
        clearInterval(intervalPremio1)
        clearInterval(intervalPremio2)
        clearInterval(intervalPremio3)
        this.alertarUsuario()
      }, 2000)
    },
    alertarUsuario () {
      if (this.$store.state.premios.premio1 === '$' && this.$store.state.premios.premio2 === '$' && this.$store.state.premios.premio3 === '$') {
        this.$store.state.premios.vencedor = 'Parabens, voce ganhou um desconto'
      } else {
        this.$store.state.premios.vencedor = 'Nao foi dessa vez, tente novamente'
      }
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 20px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#painel {
  background-color: chocolate;
  width: 500px;
  height: 300px;
  align-items: center;
  margin-left: 37%;
}

#caixa1 {
  background-color: darkgray;
  width: 100px;
  height: 200px;
  align-items: center;
  font-size: 7em;
  color: #1600db;
}

#caixa2 {
  background-color: darkgray;
  width: 100px;
  height: 200px;
  align-items: center;
  font-size: 7em;
  color: #db0000;
}

#caixa3 {
  background-color: darkgray;
  width: 100px;
  height: 200px;
  align-items: center;
  font-size: 7em;
  color: #dbcc00;
}
</style>
