<template>
  <div>
    <div class="container">
      <div class="mail-box">
        <app-sidebar :messages="messages"></app-sidebar>
        <app-content></app-content>
      </div>
    </div>
  </div>
</template>

<script>
  import Sidebar from './components/Sibebar.vue'
  import Content from './components/Content.vue'
  //importation des data (API)
  import messages from '../src/data/messages'

export default {
  data(){
    return {
      //inclusion des data
      messages : messages
    }
  },

  components: {
    appSidebar: Sidebar,
    appContent: Content
  }
}
</script>
