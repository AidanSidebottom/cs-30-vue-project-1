<script setup>

import{ref, computed} from 'vue'
//import assets from '../src/assets'

const player = ref('white')
const movesList = ref([])
let holding = false;
let choosePeice;

const board = ref([
  ['bc','bh','bb','bk','bq','bb','bh','bc'],
  ['bp','bp','bp','bp','bp','bp','bp','bp'],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['wp','wp','wp','wp','wp','wp','wp','wp'],
  ['wc','wh','wb','wk','wq','wb','wh','wc'],
])

const checker = (x,y)=>{
if((x+y)%2==0)
{
  return 'white'
  }
  else{
  return 'black'
  }
}



const turn = (x,y)=>{
  if(holding===false){
  player.value = player.value === 'white'? 'black' :'white'
  choosePeice = board.value[x][y];
  holding=true
  board.value[x][y] = '';
  }else{
  board.value[x][y]=choosePeice
  holding=false;
  movesList.value.push(choosePeice+' '+x+' '+y)
  }
  return 
}

const resetGame = ()=>{
  board.value =
  [
  ['br','bh','bb','bk','bq','bb','bh','br'],
  ['bp','bp','bp','bp','bp','bp','bp','bp'],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['wp','wp','wp','wp','wp','wp','wp','wp'],
  ['wr','wh','wb','wk','wq','wb','wh','wr'],
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
          v-bind:class="checker(x,y)"
          

        >
          <div>
          {{board[x][y]}}
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
.white:hover{
  background-color: rgb(180, 76, 16);
}
.black:hover{
  background-color: rgb(180, 76, 16);
}

</style>
