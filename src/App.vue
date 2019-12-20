<template>
  <div id="app">
    <label>Qtd. Cartelas: </label>
    <input v-model="cartelas"/>
    <hr />
    <label>Qtd. Números/cartela: </label>
    <input v-model="numeros"/>
    <hr />
    <h4>Resultado:</h4>
    <table>
      <tr v-for="(jogo, idx) in jogos" :key="idx">
        <td v-for="j in jogo" :key="j">{{j}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  created() {
    while (this.jogos.length < this.cartelas) {
      const arr = [];
      while (arr.length < this.numeros) {
        let random = Math.floor(Math.random() * 60) + 1;
        if (arr.indexOf(random) === -1) arr.push(random);
      }
      this.jogos.push(arr.sort((a, b) => a - b));
    }
  },
  data() {
    return {
      jogos: [],
      cartelas: 10,
      numeros: 8
    };
  }
};
</script>

<style lang="scss">
#app {
  table {
    border: 1px solid;
    text-align: center;
    tr {
      &:nth-child(2n) {
        background-color: gray;
      }
      td {
        border: 1px solid;
        padding: 5px;
      }
    }
  }
}
</style>
