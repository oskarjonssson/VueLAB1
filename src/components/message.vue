<template>
	<div>
		<p >{{errorMessage}}</p>
	</div>
</template>

<script>
export default {
  props:['errorMessage']
}
</script>

<style scoped>
  input{
    margin: 0 10px 0 0;
  }
div{
  background-color: #ff3838;
  z-index: 2;
  position: absolute;
  top: 20px;
  right: 40px;
  width: 250px;
  border-radius: 3px;
  height: 40px;
  color: #fff;
}


</style>
