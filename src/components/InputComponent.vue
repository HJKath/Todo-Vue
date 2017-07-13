<template>
  <div id="inputComp">
    <div class="wrap-input">
      <input class="input-todo" type="text" v-model="todoValue" v-on:keyup.enter="addItem" placeholder="할 일을 입력하세요"/>
      <button class="btn-confirm" v-on:click="addItem">
        <i class="fa fa-plus"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['passedData'],
  data () {
    return {
      msg: 'this is a input component',
      todoValue: ''
    }
  },
  methods: {
    // ### addItem : 입력 ###
    addItem() {
      console.log(">>> add item = " + this.todoValue);

      if (this.todoValue != undefined && this.todoValue.length > 0) {
        if (localStorage.getItem(this.todoValue) != null) {
          alert("이미 등록 된 할 일 입니다.");
          return;
        }

        var value = this.todoValue && this.todoValue.trim();
        localStorage.setItem(value, value);
        this.passedData.push(value);

        // this.todoValue = '';
        this.clearForm();
      }
    }
    // ### clearForm : 입력 데이터 초기화 ###
    ,clearForm() {
      this.todoValue = '';
    }

  },
}
</script>

<style lang="css">
.wrap-input {
  display: flex;
  height: 36px;
  margin-bottom: 5px;
  padding: 0
}
.input-todo {
  width: calc(100% - 77px);
  height: 34px;
  margin: 0;
  padding: 0 12px;
  border: 1px solid #ccc;
  margin-bottom: 5px;
}
.btn-confirm {
  width: 50px;
  height: 36px;
  background-color: #009A65;
  border: none;
  padding: 0;
  margin: 0;
}
.btn-confirm > i {
  font-size: 16px;
  color: #fff;
}
</style>
