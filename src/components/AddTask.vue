<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>

    <div class="form-control">
      <label for="dateTimeInput">Select Date and Time:</label>
      <input 
      type="datetime-local" 
      v-model="datetime"
      id="dateTimeInput" 
      />

    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Add Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: '',
      datetime:'',
      reminder: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.text) {
        alert('Please add a task')
        return
      }

      const newTask = {
        text: this.text,
        datetime: this.datetime,
        reminder: this.reminder,
      }

      this.$emit('add-task', newTask)

      this.text = ''
      this.datetime = ''
      this.reminder = false
    },
  },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}


</style>
