<template>
  <div>
    <h2>TodoList</h2>
    <!-- Input -->
    <div class="input-container">
      <form>
        <input type="text" v-model="task" placeholder="Enter your task">
        <button type="submit" @click="submitTask">SUBMIT</button>
      </form>
    </div>
    <!-- Task -->
    <table>
      <tbody>
        <tr v-for="(task,index) in tasks" :key="index">
          <td>
            <input type="checkbox">
          </td>
          <td>
            <span :class="{'finished': task.status === 'finished'}">
              {{task.name}}
            </span>
          </td>
          <td>
            <span @click="editTast(index)">
              <i class="fa fa-pen"></i>
            </span>
          </td>
          <td>
            <span @click="deleteTask(index)">
              <i class="fa fa-trash"></i>
            </span>
          </td>
          <td>
            <span v-if="tasks[index].status === 'normal'" @click="changeStatus(index)">
              <i class="far fa-star"></i>
            </span>
            <span v-else @click="changeStatus(index)">
              <i class="fas fa-star"></i>
            </span>
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
    msg: String,
  },
  data() {
    return {
      task: '',
      editedTask: null,
      checkStatus: true,
      availableStatuses: ['normal', 'asap'],

      tasks: [
        {
          name: '바나나 먹기',
          status: 'normal'
        },
        {
          name: '방청소 하기',
          status: 'asap'
        }
      ]
    }
  },
  methods: {
    submitTask() {
      if(!this.task.length) {
        alert('할일을 입력해주세요!');
      } else {
        if(!this.editedTask) {
          this.tasks.push({
            name: this.task,
            status: 'normal'
          })
        } else {
          this.tasks[this.editedTask].name = this.task;
          this.editedTask = null;
        }
        event.preventDefault();
        this.task = '';
      }

    },
    deleteTask(index) {
      this.tasks.splice(index,1);
    },
    editTast(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    changeStatus(index){
      if(this.tasks[index].status === 'normal') {
        this.tasks[index].status = 'asap';
        console.log(this.tasks[index]);
        // 왜 status가 변경이 안될까?!!
      } 
    }
  },
  computed: {
    
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
span {
  cursor: pointer;
}
form {
  display: flex;
  width: 60%;
}
.input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px 0;
}
.input-container > form > input {
  width: 90%;
  height: 50px;
  border: 1px solid #ccc;
  text-indent: 10px;
  font-size: 18px;
}
.input-container > form > button {
  border: none;
  width: 10%;
  height: 50px;
  font-size: 1vw;
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
.finished {
  text-decoration: line-through;
}
</style>
