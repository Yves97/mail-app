<template>
  <div>
    <div class="container">
      <div class="mail-box">
        <app-sidebar></app-sidebar>
      </div>
    </div>
  </div>
</template>

<script>
  import Sidebar from './components/Sibebar.vue'

export default {
  components: {
    appSidebar: Sidebar
  }
}
</script>
