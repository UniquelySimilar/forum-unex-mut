<template>
  <div id="app" class="container">
    <mail-list />
  </div>
</template>

<script>
  import MailList from '@/components/MailList'

  export default {
    name: 'App',
    components: {
      MailList
    }
  }
</script>

<style>
  #app {
    margin-top: 40px;
  }
</style>