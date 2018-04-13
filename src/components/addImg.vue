<template>
  <div>
    <img v-bind:src="url" />
  </div>
</template>

<script>
export default {
  props: ['url']
}
</script>

<style scoped>
img{
  width: 50px;
}
div{
  padding: 0;
  margin: 0;
  display: flex;
  align-items: center;
}
</style>
