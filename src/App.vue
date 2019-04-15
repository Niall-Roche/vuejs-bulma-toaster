<template>
  <div id="app">
    <toaster @close="showToast=!showToast"
             :show="showToast"
             :type="type"
             :position="position"
             :title="title"
             :message="message">
    </toaster>
    <section class="section">
      <div class="columns">
        <div class="column is-6 is-offset-3 has-text-centered">
          <h1 class="title has-text-primary">VueJS Toaster With Bulma</h1>
        </div>
      </div>
      <div class="columns">
         <div class="column is-half is-offset-one-quarter">
           <div class="columns">
             <div class="column is-half">
               <p class="is-pulled-left">Position</p>
               <div class="select is-fullwidth">
                 <select v-model="position">
                   <option selected disabled value="">Please select a position</option>
                   <option value="top-left">Top Left</option>
                   <option value="top-middle">Top Middle</option>
                   <option value="top-right">Top Right</option>
                   <option value="bottom-left">Bottom Left</option>
                   <option value="bottom-middle">Bottom Middle</option>
                   <option value="bottom-right">Bottom Right</option>
                 </select>
               </div>
             </div>
             <div class="column is-half">
               <p class="is-pulled-left">Type</p>
               <div class="select is-fullwidth">
                 <select v-model="type">
                   <option disabled value="">Please select one</option>
                   <option value="success">Success</option>
                   <option value="warning">Warning</option>
                   <option value="danger">Danger</option>
                   <option value="info">Info</option>
                   <option value="primary">Primary</option>
                 </select>
               </div>
             </div>
           </div>
         </div>
      </div>
      <div class="columns">
        <div class="column is-half is-offset-one-quarter">
          <input v-model="title" class="input" type="text" placeholder="Title">
        </div>
      </div>
      <div class="columns">
        <div class="column is-half is-offset-one-quarter">
          <input v-model="message" class="input" type="text" placeholder="Message">
        </div>
      </div>
      <div class="columns">
        <div class="column is-half is-offset-one-quarter">
          <a @click="showToast=!showToast" class="button has-text-grey-lighter is-large is-fullwidth has-background-dark">SHOW TOAST</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Toaster from '@/components/Toaster.vue'

export default {
  name: 'app',
  components: {
    Toaster
  },
  data () {
    return {
      title: null,
      message: null,
      position: null,
      type: null,
      showToast: false
    }
  }
}
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
