<template>
  <div>
    <h2>TodoList</h2>
    <!-- Input -->
    <div class="input-container">
      <input type="text" placeholder="Enter your task">
      <button @click="submitTask">SUBMIT</button>
    </div>
    <!-- Task -->
    <table>
      <tbody>
        <tr v-for="(task,index) in tasks" :key="index">
          <td>
            <input type="checkbox">
          </td>
          <td>
            {{task.name}}
          </td>
          <td>
            <span class="fa fa-pen"></span>
          </td>
          <td>
            <span class="fa fa-trash"></span>
          </td>
          <td>
            <span class="far fa-star"></span>
            <span class="fas fa-star"></span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    msg: String
  },
  data() {
    return {
      tasks: [
        {
          name: '바나나 먹기',
          status: 'asap'
        },
        {
          name: '방청소 하기',
          status: 'normal'
        }
      ]
    }
  },
  methods: {
    submitTask() {
      console.log('hello from submit button');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing: border-box;
}
table {
  margin: 0 auto;
  width: 60%;
  border-collapse: collapse;
  text-align: center;
}
h2 {
  margin-top: 80px;
  text-align: center;
}
.input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px 0;
}
.input-container > input {
  width: 50%;
  height: 50px;
  border: 1px solid #ccc;
  text-indent: 10px;
  font-size: 18px;
}
.input-container > button {
  padding: 0 20px;
  border: none;
  height: 50px;
  font-size: 18px;
}
table > tbody > tr {
  height: 50px;
  border: 1px solid #ccc;
}
table > tbody > tr > td:nth-of-type(1) {
  width: 50px;
}
table > tbody > tr > td:nth-of-type(2) {
  text-align: left;
  text-indent: 10px;
}
table > tbody > tr > td:nth-of-type(3) {
  width: 10%;
}
table > tbody > tr > td:nth-of-type(4) {
  width: 10%;
}
table > tbody > tr > td:nth-of-type(5) {
  width: 10%;
}
</style>
