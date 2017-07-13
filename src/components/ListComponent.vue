<template>
  <div id="listComp">
    <table v-if="passedData">
      <colgroup>
				<col style="width: 10%" />
				<col style="width: 80%" />
				<col style="width: 10%" />
			</colgroup>
      <tbody>
        <tr v-for="(item, index) in passedData" :key="item">
          <td class="td-align-center">
            <div class="wrap-round">
              {{index+1}}
            </div>
          </td>
          <td>{{item}}</td>
          <td class="td-align-right">
            <button class="btn-remove" v-on:click="removeItem(index)">
              <i class="fa fa-times"></i>
            </button>
          </td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
export default {
  props: ['passedData']
  ,data () {
    return {
      // msg: 'this is a list component'
    }
  }
  ,methods: {
    removeItem(index) {
      console.log(index);
      // var key = this.passedData[index];
      // localStorage.removeItem(key);
      // this.passedData.splice(index, 1);
      this.$emit('removeItem', index);
    }
  }
}
</script>

<style scoped>
  table {
    width:100%;
    padding: 0;
    text-align: left;
    border-collapse: separate;
    border-spacing: 0 5px;
    font-size: 14px;
  }
  table > tbody > tr > td {
    border-top: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
    padding: 5px;
  }
  table > tbody > tr > td.td-align-center {
    text-align: center;
  }
  table > tbody > tr > td.td-align-right {
    text-align: right;
    padding-right: 0;
  }

  .wrap-round {
    width: 24px;
    height: 24px;
    line-height: 24px;
    border: none;
    border-radius: 50%;
    background-color: RGBA(63, 189, 227, 0.6);
    color:#fff;
  }

  .btn-remove {
    width: 50px;
    height: 36px;
    background-color: #E07B5F;
    border: none;
  }
  .btn-remove > i {
    font-size: 16px;
    color: #fff;
  }
</style>
