<script setup>
import{ref,computed} from 'vue'
const player = ref('x')
const board = ref([
  ['c','h','b','k','q','b','h','c'],
  ['p','p','p','p','p','p','p','p'],
  ['','','','','','','',''],
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
        class = "cell"
      >
     
      </div>
     </div>
  </main>
 
    
</template>



<style scoped>
.board{
  
}
.cell{
  display:inline-block;
  vertical-align:middle;
  background-color:lightgreen;
  border: white;
  border-radius: 10px;
  height:10px;
  width:10px;
  background-color: rgb(126, 51, 51);
  
  padding:10px;
}
.player{
  padding: 10px;
  font-size: 20px;
  
}

</style>
