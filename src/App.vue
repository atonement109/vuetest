<template>
  <div>
    <HeaderAce></HeaderAce>
    <p v-if="msg.length > 0">
      {{msg}}
    </p>

    <p v-else>
      no text
    </p>
    <input type="text" v-model="msg">
    <button @click="clear()">clear</button>
  </div>
</template>


<script>
import HeaderAce from './components/HeaderAce.vue'

export default {
  components: {
    HeaderAce
  },
  data () {
    return {
      msg: 'Hello World!'
    }
  },
  methods: {
    clear () {
      this.msg = ''
    }
  },
  created () {
    fetch('https://fakestoreapi.com/products/1')
    .then( response => {
      return response.json()
    })
    .then( json => {
      this.msg = json.title
    })
    .catch( (err) => {
      this.msg = err // エラー処理
    });
  }
}
</script>
