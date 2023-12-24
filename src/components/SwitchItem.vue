<script>
import { ref, computed } from 'vue'
import AdminItem from './Users/AdminItem.vue'
import DistinguishedItem from './Users/DistinguishedItem.vue'
import GuestUser from './Users/GuestUser.vue'
import SelectItem from './SelectItem.vue'

export default {
  components: {
    SelectItem
  },
  setup() {
    const user = ref('')

    const changeComponent = computed(() => {
      const myComponent = {
        admin: AdminItem,
        distiguished: DistinguishedItem,
        guest: GuestUser
      }

      return myComponent[user.value] ?? GuestUser
    })

    const setUserChange = (newUser) => (user.value = newUser)

    return {
      user,
      changeComponent,
      setUserChange
    }
  }
}
</script>

<template>
  <SelectItem @change-user="setUserChange" />

  <component :is="changeComponent" :msg="`${user} information`">
    <p style="width: 200px; height: 4vh">I am a {{ user }} user</p>
  </component>
</template>
