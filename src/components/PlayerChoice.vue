<template>
<div class='buttons' id="buttons">
  <button class="btn btn-primary" name="pedra" @click="pick($event)">Pedra</button>
  <button class="btn btn-primary" name="papel" @click="pick($event)">Papel</button>
  <button class="btn btn-primary" name="tesoura" @click="pick($event)">Tesoura</button>
</div>
  <div class="d-flex justify-content-around">
    <img v-if="playerPick !== ''" :src="require(`../assets/${playerPick}.png`)" />
    <img v-if="playerPick !== ''" :src="require(`../assets/${cpuPick[cpuPickPos]}.png`)" />
  </div>
  <span>{{ resultado }}</span>
  <h2>Placar</h2>
  <div class="d-flex justify-content-around">
    <span>{{ playerScore }}</span>
    <p> x </p>
    <span>{{ cpuScore}}</span>
  </div>
</template>

<script>
export default {
  name: 'PlayerChoice',
  data () {
    return {
      playerPick: '',
      cpuPick: ['pedra', 'papel', 'tesoura'],
      cpuPickPos: 0,
      resultado: '',
      playerScore: 0,
      cpuScore: 0
    }
  },
  methods:{
    pick(e) {
      console.log(Math.floor(Math.random() * 3));
      this.cpuPickPos = Math.floor(Math.random() * 3);
      this.playerPick = e.target.name;
      if(this.playerPick === this.cpuPick[this.cpuPickPos]) {
        this.resultado = 'empate'
      } else if(this.playerPick === 'pedra' && this.cpuPick[this.cpuPickPos] === 'papel' ) {
        this.cpuScore += 1
        this.resultado = 'perdeu'
      } else if(this.playerPick === 'papel' && this.cpuPick[this.cpuPickPos] === 'tesoura' ) {
        this.cpuScore += 1
        this.resultado = 'perdeu'
      } else if(this.playerPick === 'tesoura' && this.cpuPick[this.cpuPickPos] === 'pedra' ) {
        this.cpuScore += 1
        this.resultado = 'perdeu'
      } else {
        this.playerScore += 1
        this.resultado = 'ganhou'
      }
    }
  }
}
</script>