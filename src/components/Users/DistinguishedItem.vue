<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>
<template>
  <div class="item">
    <div>Distiguished Component</div>
    <h1>{{ msg }}</h1>
    <div>
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.item {
  width: 400px;
  height: 20vh;
  background-color: firebrick;
  color: white;
  border: 1px solid grey;
  border-radius: 1em;
  padding: 1em;
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
}
</style>
