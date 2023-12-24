<script>
import { ref, defineComponent } from 'vue'

export default defineComponent({
  setup(_, context) {
    const user = ref('guest')

    const emitUserChange = () => {
      
      context.emit('change-user', user.value);
    }

    return {
      user,
      emitUserChange
    }
  }
})
 
</script>

<template>
  <select v-model="user" @change="emitUserChange">
    <option value="admin">Admin</option>
    <option value="guest">Guest</option>
    <option value="distiguished">Distiguished</option>
  </select>
  <p>{{ user }}</p>
</template>
