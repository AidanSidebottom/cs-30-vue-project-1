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
  <main class="Board">
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
.cell{
  border: white;
  border-radius: 10px;
  height:20px;
  width:20px;
  background-color: black;
  padding:10px;
  align-items: center;
  justify-content: center;
}
.player{
  padding: 10px;
  font-size: 20px;
  
}

</style>
