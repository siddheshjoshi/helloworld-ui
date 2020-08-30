<template>
  <div class="home">
    Enter Name <input v-model="name"  />
    &nbsp;<button @click="submit()"> Submit </button>
    &nbsp;<span v-if="respn">{{respn.data}}</span>
  </div>
</template>

<script>
// @ is an alias to /src
import api from "@/api/index.js"

export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      name: undefined,
      respn: undefined
    }
  },
  methods: {
    submit() {
      console.log("submitting name: ", this.name)
      api.get("https://frosty-ritchie-functions.netlify.app/.netlify/functions/hello-world?name="+ this.name).then(resp => {
        this.respn=resp
      }).catch(err => {
        this.respn=err
      })
      
    }
  }
}
</script>
