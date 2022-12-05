<script setup>
import{ref,computed} from 'vue'
const player = ref('white')
const color = ref('white')
const board = ref([
  ['c','h','b','k','q','b','h','c'],
  ['p','p','p','p','p','p','p','p'],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['','','','','','','',''],
  ['p','p','p','p','p','p','p','p'],
  ['c','h','b','k','q','b','h','c'],
])


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
        class = "white"

      >
        <div>
        {{board[x][y]}}
        </div>
      </div>
     </div>
  </main>
 
    
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
  background-color: rgb(81, 158, 115);
  padding:10px;
}
.black{
  display:inline-block;
  vertical-align:middle;
  border: 3px solid white;
  border-radius: 3px;
  height:20px;
  width:20px;
  background-color: rgb(3, 17, 9);
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
