<template>
  <div class="home">
      <i>"{{quote}}"</i>
      <p>-Kanye West</p>

      <button @click="getData">Change Quote</button>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import {ref} from 'vue'
export default {
  name: 'HomeView',
  components: {
  
  },
  setup () {
    let quote = ref('');
     return{
      quote
     }
  },
  mounted() {
    this.getData()
  }, 
  methods: {
     getData(){
        axios.get('https://api.kanye.rest/').then(response => {
        // handle response
        this.quote = response.data.quote
       })
     }
  }
}
</script>
