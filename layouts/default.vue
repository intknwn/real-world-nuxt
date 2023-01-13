<template>
  <div id="app">
    <NavBar />
    <Nuxt />
  </div>
</template>

<script>
import NavBar from '~/components/NavBar.vue'

export default {
  components: { NavBar },
  head() {
    return {
      titleTemplate: '%s — Real World Events',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Where you can find all events taking place in your neighborhood',
        },
      ],
    }
  },
}
</script>
