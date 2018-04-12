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
    margin: 0 10px 0 0;
  }

</style>
