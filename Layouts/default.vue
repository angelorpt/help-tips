<template>
  <div>
    <NavBar />
    <Nuxt />
  </div>
</template>

<script>
import NavBar from '@/components/molecules/Navbar.vue'

export default {
  name: 'DefaultLayout',
  components: { NavBar },
  props: {},
  data() {
    return {}
  },
}
</script>

<style lang="class-name" scoped></style>
