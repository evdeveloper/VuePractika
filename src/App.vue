<template>
  <div id="app">
    <my-components/>
    <user-card />
  </div>
</template>

<script>

// import MyComponents from './components/MyOneComponents'
import UserCard from './components/UserCard'

export default {
  name: 'App',
  components: {
    // MyComponents,
    UserCard
  }
}
</script>

