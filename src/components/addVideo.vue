<template>
  <div>
    <iframe allowfullscreen frameborder="0" v-bind:src="video" ></iframe>
  </div>
</template>

<script>
export default {
  props: ['video']
}
</script>

<style>
  iframe{
    height: 220px;
    width: 520px;
    margin-left: 10px;
  }
</style>
