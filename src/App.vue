<template>
  <div id="app">
    <InputComponent v-bind:passedData="todoItems"></InputComponent>
    <ListComponent v-bind:passedData="todoItems"></ListComponent>
  </div>
</template>

<script>
import InputComponent from './components/InputComponent.vue'
import ListComponent from './components/ListComponent.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
      ,todoItems : []
    }
  }
  // Component Registration
  ,components : {
    ListComponent: ListComponent
    ,InputComponent: InputComponent
  }
  ,created() {
    for(var key in localStorage) {
      console.log(">>> 리스트 가녀오는 중 = " + localStorage.getItem(key));

      this.todoItems.push(localStorage.getItem(key));
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 20px;
}

</style>
