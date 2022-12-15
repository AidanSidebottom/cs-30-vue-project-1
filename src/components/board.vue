<script setup>

import{ref, computed} from 'vue'
//import assets from '../src/assets'

const player = ref('white')
const movesList = ref([])
let holding = false;
let choosePeice;
const br = {name:"Black Rook",color:"blackPcs",symbol:"♜"}
const bh = {name:"Black Horse",color:"blackPcs",symbol:"♞"}
const bb = {name:"Black Bishop",color:"blackPcs",symbol:"♝"}
const bk = {name:"Black King",color:"blackPcs",symbol:"♚"}
const bq = {name:"Black Queen",color:"blackPcs",symbol:"♛"}
const bp = {name:"Black Pawn",color:"blackPcs",symbol:"♟︎"}

const wr = {name:"White Rook",color:"whitePcs",symbol:"♖"}
const wh = {name:"White Horse",color:"whitePcs",symbol:"♘"}
const wb = {name:"White Bishop",color:"whitePcs",symbol:"♗"}
const wk = {name:"White King",color:"whitePcs",symbol:"♔"}
const wq = {name:"White Queen",color:"whitePcs",symbol:"♕"}
const wp = {name:"White Pawn",color:"whitePcs",symbol:"♙"}


const board = ref([
  [br,bh,bb,bq,bk,bb,bh,br],
  [bp,bp,bp,bp,bp,bp,bp,bp],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  [wp,wp,wp,wp,wp,wp,wp,wp],
  [wr,wh,wb,wq,wk,wb,wh,wr],
])
const tiles = (x,y)=>{

if((x+y)%2==0){
    return 'white'
  }
  else{
    return 'black'
  }
}
// const legalMoves = (x,y) =>{
//   if(choosePeice.name === "Black Rook"){
//      if (x===x&&y!=y||y===y&&x!=x){
//        return true
//      }else{
//        alert('invalid move');
//        return false
//      }
//   }
// }

const turn = (x,y)=>{
  if(holding===false){
    choosePeice = board.value[x][y];
    board.value[x][y] = '';
    holding=true
  }else{
    player.value = player.value === 'white'? 'black' :'white'
    board.value[x][y]=choosePeice
    holding=false;
    movesList.value.push(board.value[x][y].name+' '+x+' '+y)
  }
  return 
}

const resetGame = ()=>{
  board.value =
  [
  [br,bh,bb,bq,bk,bb,bh,br],
  [bp,bp,bp,bp,bp,bp,bp,bp],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  [wp,wp,wp,wp,wp,wp,wp,wp],
  [wr,wh,wb,wq,wk,wb,wh,wr],
];
player.value='white';
holding=false;
movesList.value = []
choosePeice=[]
}


</script>
 
<template>
  <div class=player>
    The current player Is {{player}}
  </div>
    <main class="board">
      <div
        
        v-for="(row, x) in board"
        :key="x"
      >
        <div 
          v-for="(cell, y) in row"
          :key="y"
          @click="turn(x,y)"
          v-bind:class="tiles(x,y)"
          

        >
          <div
           v-bind:class="board[x][y].color"
           >
          {{board[x][y].symbol}}
          </div>
        </div>
      </div>
    </main>

  <button @click="resetGame()">
    Reset game 
  </button>

  <div>
    Moves: {{movesList}}
  </div>
  
    
</template>



<style scoped>
.board{
  margin: auto;
  width: 50%;
}
.white{
  display:inline-block;
  vertical-align:middle;
  border: 3px solid white;
  border-radius: 3px;
  height:20px;
  width:20px;
  background-color: rgb(127, 160, 142);
  padding:10px;
}
.black{
  display:inline-block;
  vertical-align:middle;
  border: 3px solid white;
  border-radius: 3px;
  height:20px;
  width:20px;
  background-color: rgb(12, 117, 61);
  padding:10px;
}
.player{
  padding: 10px;
  font-size: 20px;
  text-align: center;
}
.whitePcs{
  color: white
}
.blackPcs{
  color: black
}
.white:hover{
  background-color: rgb(180, 76, 16);
}
.black:hover{
  background-color: rgb(180, 76, 16);
}


</style>
