<template>
  <div>
    <ul>
      <li
        v-for="(item, index) in todoItems"
        v-bind:key="item.item"
        class="shadow"
      >
        <i
          class="fas fa-check checkBtn"
          v-bind:class="{ checkBtnComplated: item.complated }"
          v-on:click="toggleComplate(item, index)"
        ></i>
        <span v-bind:class="{ textComplated: item.complated }">{{
          item.item
        }}</span>
        <span class="removeBtn" v-on:click="removeItem(item, index)"
          ><i class="fas fa-trash"></i
        ></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todoItems: [],
    };
  },
  created: function() {
    for (let i = 0; i < localStorage.length; i++) {
      if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
        this.todoItems.push(
          JSON.parse(localStorage.getItem(localStorage.key(i)))
        );
      }
    }
  },
  methods: {
    removeItem: function(item, index) {
      localStorage.removeItem(item);
      this.todoItems.splice(index, 1);
    },
    toggleComplate: function(item, index) {
      console.log(item, index);
      item.complated = !item.complated;
      // 로컬 스토리지의 데이터를 갱신
      localStorage.removeItem(item.item);
      localStorage.setItem(item.item, JSON.stringify(item));
    },
  },
  watch: {
    todoItems: function() {
      console.log('변경되었음');
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align-last: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: #fff;
  border-radius: 5px;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}

.checkBtnComplated {
  color: #b3adad;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}

.textComplated {
  text-decoration: line-through;
  color: #b3adad;
}
</style>
