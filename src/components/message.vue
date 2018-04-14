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
  background:linear-gradient(135deg, #F5515F 0%,#A1051D 100%);
	font-size: 13px;
	font-family: 'Montserrat', sans-serif;
  z-index: 2;
  position: absolute;
  top: 20px;
  right: 40px;
  width: 250px;
  border-radius: 5px;
  height: 40px;
  color: #fff;
}

</style>
