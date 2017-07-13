<template>
  <div id="FooterComp">

    <button class="btn-clear" v-on:click="clearLocalStorage">Clear All</button>

    </div>
  </div>
</template>

<script>
export default {
  // props: ['passedData'],
  data () {
    return {

    }
  },
  methods: {
    clearLocalStorage () {
      this.$emit('clearLocalStorage');
    }

  },
}
</script>

<style lang="css">
  .btn-clear {
    width: 100%;
    height: 34px;
  }
</style>
