<template>
  <q-page class="bg-black-3 column">
    <img
      alt="logo"
      src="../assets/welcome.gif "
      style="width: 404px; height: 110px; align-self: center">
    <div class="row q-pa-sm bg-black">

      <q-input standout v-model="newTask" dense placeholder="new task" @keyup.enter="addTask">
        <template v-slot:append>
          <q-avatar @click="addTask">
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo.svg">
          </q-avatar>
        </template>
      </q-input>

    </div>
    <q-list
      separator
      bordered>
      <q-item
        @click="task.done = !task.done"
        clickable
        v-ripple
        v-for="(task, index) in tasks" :key="task.title"
        :class="{'done bg-green-1': task.done}">
        <q-item-section avatar>
          <q-checkbox
            class="no-pointer-events"
            v-model="task.done" val="teal" color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
        v-if="task.done" side>
          <q-btn @click.stop="deleteTask(index)" color="amber" glossy label="Delete" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data(){
    return{
      newTask: "",
      tasks: [
        {
          title: 'to pet cat',
          done: false
        },
        {
          title: 'to pet dog',
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask(index){

      this.$q.dialog({
        dark: true,
        title: 'Confirm',
        message: 'Really?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index, 1)
        this.$q.notify({
          type: 'positive',
          message: 'Deleted.'
      });
    })
  },
    addTask(){
      this.tasks.push({
        title: this.newTask,
        done: false,
      });
      this.newTask=""
    }
  }
}

</script>
<style lang="scss">
.done{
  .q-item__label{
    text-decoration: line-through;
    color: #9C27B0;
  }
}
</style>
