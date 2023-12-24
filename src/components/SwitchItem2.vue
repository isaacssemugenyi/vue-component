<script>
import { ref } from 'vue'
import AdminItem from './Users/AdminItem.vue'
import DistinguishedItem from './Users/DistinguishedItem.vue'
import GuestUser from './Users/GuestUser.vue'
import SelectItem from './SelectItem.vue'

export default {
  setup() {
    const user = ref('guest')

    const setUserChange = (newUser) => (user.value = newUser)

    return { user, setUserChange }
  },
  components: {
    SelectItem,
    AdminItem,
    DistinguishedItem,
    GuestUser
  }
}
</script>

<template>
  <h1 style="margin-top: 2em">Using IF Statement</h1>
  
  <SelectItem @change-user="setUserChange" />

  <template v-if="user === 'admin'">
    <AdminItem :msg="`${user} information`">
      <p style="width: 200px; height: 4vh">I am an {{ user }} user</p>
    </AdminItem>
  </template>

  <template v-else-if="user === 'guest'">
    <GuestUser :msg="`${user} information`">
      <p style="width: 200px; height: 4vh">I am a {{ user }} user</p>
    </GuestUser>
  </template>

  <template v-else>
    <DistinguishedItem :msg="`${user} information`">
      <p style="width: 200px; height: 4vh">I am a {{ user }} user</p>
    </DistinguishedItem>
  </template>
</template>
