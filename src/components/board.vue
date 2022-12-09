<script setup>

import{ref, computed} from 'vue'
const player = ref('white')
const movesList = ref(["startingPos",])
let holding = true;
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
if(x+y===0||x+y===2||x+y===4||x+y===6||x+y===8||x+y===10
||x+y==12||x+y===14)
//For some reason checking if the number was even did not seem to work
{
  return 'white'
  }
  else{
  return 'black'
  }
}



const turn = (x,y)=>{
  if(holding===true){
  player.value = player.value === 'white'? 'black' :'white'
  choosePeice = board.value[x][y];
  holding=false
  board.value[x][y] = '';
  }else{
  board.value[x][y]=choosePeice
  holding=true;
  }
  //movesList.push("a move")
  return 
}

const resetGame = ()=>{
  board.value =
  [
  ['bc','bh','bb','bk','bq','bb','bh','bc'],
  ['bp','bp','bp','bp','bp','bp','bp','bp'],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['wp','wp','wp','wp','wp','wp','wp','wp'],
  ['wc','wh','wb','wk','wq','wb','wh','wc'],
];
player.value='white';
holding=false;
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
    Moves : 
    {{movesList}}
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
