<template>
  <div>
    <form>
      <h2><u>todos</u></h2>
      <input type="text" v-model="itemAdd" @keydown.stop.prevent.enter="addTask" placeholder="What needs to be done ?">
      <p>
        已完成個數: {{completeCount}} / 未完成個數: {{todoCount}}
        &nbsp;&nbsp;&nbsp;
        <button @click="clearTask">清除</button>
      </p>
      <table>
        <tr v-for="(item, index) in itemALL" :key="index">
          <td align="left">
            <input type="checkbox" @click="checkTask(item)" :checked="item.check">&nbsp;
            <label v-if="item.check == true" style="text-decoration: line-through;color: #D3D3D3;">{{item.task}}</label>
            <label v-else>{{item.task}}</label>
            <i class="far fa-times-circle" @click="deleteTask(item)"></i>
          </td>
        </tr>
      </table>
    </form>
  </div>
</template>

<script>
export default {
  name: 'todoList',
  data() {
    return {
      itemAdd: '',
      itemALL: [],
      completeCount: 0,
      todoCount: 0,
    }
  },
  methods: {
    addTask() {
      if (this.itemAdd.trim() != '') {
        this.itemALL.push({ task: this.itemAdd, check: false });
        this.itemAdd = '';
        this.summary();
      }
    },
    deleteTask(item) {
      let index = this.itemALL.indexOf(item);
      this.itemALL.splice(index, 1);
      this.summary();
    },
    checkTask(item) {
      item.check = (item.check == false) ? true : false;
      this.summary();
    },
    clearTask() {
      this.itemALL = [];
      this.completeCount = 0;
      this.todoCount = 0;
    },
    summary() {
      this.todoCount = this.itemALL.filter(function(i) { return i.check == false; }).length;
      this.completeCount = this.itemALL.filter(function(i) { return i.check == true; }).length;
    },
  }
}
</script>

<style scoped>
h2 {
  color: #8494A4;
}

p {
  font-size: 12px;
  color: #C21414;
}

button {
  font-size: 12px;
  padding: 0px;
}

input[type="text"] {
  width: 200px;
}

input:focus{
  outline: none;
}

table{
  width: 200px;
  margin: 10px auto;
}

td {
  height: 28px;
  position: relative;
  display: flex;
  align-items: center;
}

td i {
  font-size: 12px;
  position: absolute;
  right: 0;
  color: #C21414;
}
</style>
