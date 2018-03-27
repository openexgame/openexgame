<template>
  <v-app id="app">
    <app-header v-if="showCommonHeader"></app-header>
    <!--Content-->
    <transition name="fade">
      <router-view></router-view>
    </transition>
  </v-app>
</template>

<script>
import AppHeader from '@/components/Header'
import AdminPanel from './components/admin/AdminPanel'

export default {
  name: 'App',
  components: {
    AppHeader,
    AdminPanel
  },
  data () {
    return {}
  },
  computed: {
    showCommonHeader () {
      return !this.$router.history.current.fullPath.includes('admin') &&
          this.$router.history.current.fullPath !== '/'
    }
  }
}
</script>

<style lang="sass">
  body, html
    margin: 0
    padding: 0

    #app
      font-family: Montserrat, 'Avenir', Helvetica, Arial, sans-serif
      -webkit-font-smoothing: antialiased
      -moz-osx-font-smoothing: grayscale
      background-color: white
      text-align: center
      color: #2c3e50

    .fade-enter-active, .fade-leave-active
      transition-property: opacity
      transition-duration: .25s

    .fade-enter-active
      transition-delay: .25s

    .fade-enter, .fade-leave-active
      opacity: 0
</style>
