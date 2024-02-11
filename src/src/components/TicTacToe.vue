<template>
  <div>
    <div class="center">
      <div class="game">
        <div class="grid">
          <button v-for="(cell, index) in board" :key="index" class="cell" @click="makeMove(index)">
            {{ cell }}
          </button>
        </div>
        <div class="controls">
          <div class="buttons">Restart</div>
          <div class="buttons">X</div>
          <div class="buttons">O</div>
          <div class="buttons">Reset</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TicTacToe',
  data() {
    return {
      board: Array(9).fill(''),
      player: 'X',
      winner: ''
    }
  },
  methods: {
    makeMove(index) {
      if (this.board[index] === '' && !this.winner) {
        this.board[index] = this.player;
        this.player = this.player === 'X' ? 'O' : 'X';
      }
    }
  }
}
</script>

<style scoped>
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.game {
  display: flex;
  justify-content: flex-end;
  flex-wrap: nowrap;
  flex-direction: column;
  align-content: flex-start;
  align-items: center;
}

.controls {
  display: flex;
  justify-content: center;
  flex-direction: row;
}

.buttons {
  margin: 50px;
}

.buttons:hover {
  cursor: pointer;
}

.cell {
  width: 100px;
  height: 100px;
  border: 1px solid black;
  background: none;
  color: inherit;
  text-align: center;
  -webkit-appearance: none;
  -moz-appearance: none;
  transition: 0.5s;
}

.cell:hover {
  cursor: pointer;
  background: lightgray;
  transition: 0.5s;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
.grid :nth-child(1){
  border-top: none;
  border-left: none;
}
.grid :nth-child(2){
  border-top: none;
}
.grid :nth-child(3){
  border-top: none;
  border-right: none;
}
.grid :nth-child(4){
  border-left: none;
}
.grid :nth-child(6){
  border-right: none;
}
.grid :nth-child(7){
  border-bottom: none;
  border-left: none;
}
.grid :nth-child(8){
  border-bottom: none;
}
.grid :nth-child(9){
  border-bottom: none;
  border-right: none;
}
</style>
