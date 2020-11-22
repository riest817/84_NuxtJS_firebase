<template>
  <div class="container">
    <!--p>{{ $store.state.message }}</p-->
    <p>{{ $store.state.hello.message }}</p>
    <!--button v-on:click="$store.commit('updateMessage')">Update</button-->
    <!--button v-on:click="$store.commit('updateMessage', 'Commit with payload')">Update</button-->
    <!--button v-on:click="$store.dispatch('updateMessageAction', 'Commit with payload')">Dispatch</button-->
    <!--button v-on:click="$store.dispatch('updateMessageAction', 'Dispatch with payload')">Dispatch</button-->
    <button v-on:click="$store.dispatch('hello/updateMessageAction', 'Dispatch with payload')">Dispatch</button>
  </div>
</template>

<script>
const axios = require('axios')
let url = 'https://jsonplaceholder.typicode.com/users'

export default {
  asyncData({ params, error }) {
    return axios.get(url)
      .then((res) => {
        return { users: res.data }
      })
      .catch ((e => {
        //console.log(e.response.status)
        error({ users: e.response.status, message: 'Error!!!!!' })
      }))
  }
}
</script>

<style>

</style>
