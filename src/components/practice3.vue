<template>
  <div>
    <form>
      <h2><u>todos</u></h2>
      <input type="text" v-model="itemAdd" @keydown.stop.prevent.enter="add" placeholder="What needs to be done ?">
      <table v-html="list">
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
      list: ''
    }
  },
  methods: {
    add() {
      if (this.itemAdd != '') {
        this.list = `${this.list}
        <tr>
          <td align="left" style="height: 28px;position: relative;display: flex;align-items: center;">
            <label>
              <input type="checkbox">&nbsp;${this.itemAdd}
            </label>
            <i class="far fa-times-circle" style="font-size: 12px;color: #C21414;position: absolute;right: 0;"></i>
          </td>
        </tr>`;
        this.itemAdd = '';
      }
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

input {
  width: 200px;
}

input:focus{
  outline: none;
}

table{
  width: 200px;
  margin: 10px auto;
}
</style>
