<script>
export default {
  data() {
    return {
      message: 'hello world',
      button:"click me",
      boardLength:64,
      thing: 1
    }
  },
  methods:{
  makeBoard(){
    let row = [],[],[],[],[],[],[],[]
    let board =[
      [row],[row],[row],[row],[row],[row],[row],[row]
    ]
    thing = board
    
    
    }
  }
}
</script>
 
<template>
  <div id="board">
  
   <div>{{message}}</div>
   <button v-on:click="hello">{{makeBoard}}</button>

  </div>
    
</template>



<style scoped>
#board {
background-color:blue;
width:100px;
height:100px;
padding:10px;
}
</style>
