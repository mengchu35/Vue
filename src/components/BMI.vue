<template>
  <div>
    <form>
      <h2><u>計算 BMI</u></h2>
      <label for="height">
        身高:&nbsp;
        <input type="text" name="height" v-model.number="height" value="">
        &nbsp;公分
      </label>
      <br><br>
      <label for="weight">
        體重:&nbsp;
        <input type="text" name="weight" v-model.number="weight" value="">
        &nbsp;公斤
      </label>
      <br><br>
      <button v-on:click.prevent="submit()">Submit</button>
      <p>{{bmi_value}}</p>
    </form>
  </div>
</template>

<script>
export default {
  name: 'BMI',
  data() {
    return {
      height: '',
      weight: '',
      bmi_value: ''
    }
  },
  methods: {
    submit() {
      if (this.height != '' && this.weight != '') {
        let bmi = this.weight / (this.height / 100) ** 2;
        if (!isNaN(bmi)) {
          this.bmi_value = bmi;
        } else {
          this.bmi_value = '請輸入數值 !';
        }
      } else {
        this.bmi_value = '請輸入身高和體重 !';
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
</style>
