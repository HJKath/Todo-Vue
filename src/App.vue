<template>
  <div id="app">
    <InputComponent v-bind:passedData="todoItems"></InputComponent>
    <ListComponent v-bind:passedData="todoItems" v-on:removeItem="removeItem"></ListComponent>
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
      console.log(">>> 리스트 가져오는 중 = " + localStorage.getItem(key));

      this.todoItems.push(localStorage.getItem(key));
    }
  }
  ,watch: {
    todoItems: {
      handler: function(todo) {
        console.log("[App.vue] changed!!");
      }
    }
  }
  ,methods: {
    removeItem(index) {
      console.log(index);
      var key = this.todoItems[index];
      this.todoItems.splice(index, 1);
      localStorage.removeItem(key);
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
