<template>
	<div class="container">
		<Header />
		<Board />
	</div>
</template>
<script>
//sub-component must be imported and then registered in "components" below
import Header from "./components/Header.vue"
import Board from "./components/Board.vue";

export default {
	components: { Header,Board, }
};
</script>

<style scoped>
body {
	background-color: rgb(50, 82, 82);
}
.container {
	margin: 8px;
}
</style>
