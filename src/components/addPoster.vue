<template>
	<div>
		<input
			type="text"
			placeholder="URL to image"
			v-model="posterUrl" />
		<button v-on:click="$emit('adding-poster', posterUrl)">Add Movie</button>
	</div>
</template>

<script>
export default {
	data: function() {
		return {
			posterUrl: ''
		};
	}
}
</script>

<style scoped>
  input{
font-family: 'Montserrat', sans-serif;
		margin: 0 10px 0 0;
	  width: 200px;
	  border-radius: 20px;
	  outline: none;
	  border: none;
	  padding: 0 0 0 10px;
	  height: 25px;

  }
	 button{
		 border: none;
		height: 25px;
		border-radius: 20px;
		width: 100px;
		color: white;
		background-color: #0be36a;
		font-family: 'Montserrat', sans-serif;

	 }

</style>
