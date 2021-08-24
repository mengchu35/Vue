<template>
  <div>
    <form>
      <h2><u>todos</u></h2>
      <input type="text" v-model="itemAdd" @keydown.stop.prevent.enter="addTask" placeholder="What needs to be done ?">
      <table>
        <tr v-for="(item, index) in itemALL" :key="index">
          <td align="left">
            <input type="checkbox">&nbsp;
            <label>{{item}}</label>
            <i class="far fa-times-circle" @click="deleteTask(index)"></i>
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
    }
  },
  methods: {
    addTask() {
      if (this.itemAdd.trim() != '') {
        this.itemALL.push(this.itemAdd);
        console.log(this.itemALL);
        this.itemAdd = '';
      }
    },
    deleteTask(index) {
      this.itemALL.splice(index, 1);
    }
  }
}
</script>

<style scoped>
h2 {
  color: #8494A4;
}

p {
  color: #C21414;
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
