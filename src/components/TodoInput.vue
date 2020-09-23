<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo" />
    <span class="addContainer" @keyup.enter="addTodo"
      ><i class="fas fa-plus addBtn"></i
    ></span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      newTodoItem: '',
    };
  },
  methods: {
    addTodo: function() {
      if (this.newTodoItem !== '') {
        const obj = {
          complated: false,
          item: this.newTodoItem,
        };
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        this.clearInput();
      }
    },
    clearInput: function() {
      this.newTodoItem = '';
    },
  },
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  max-width: 400px;
  margin: 0 auto;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  overflow: hidden;
}

.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}

.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #2ca3f8);
  display: block;
  width: 3rem;
  border-radius: middle;
}

.addBtn {
  color: #fff;
  vertical-align: middle;
}
</style>
