<template>
  <div class="clearAllContainer shadow">
    <span class="clearAllBtn" v-on:click="clearAll"> Clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    clearAll: function() {
      this.$emit('clear');
    },
  },
};
</script>

<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: #fff;
  border-radius: 5px;
  margin: 1rem auto 0;
}
.clearAllBtn {
  color: #e20303;
  display: block;
}
</style>
