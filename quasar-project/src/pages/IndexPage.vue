<template>
  <q-page class="bg-black-3 column">
    <img
      alt="logo"
      src="../assets/welcome.gif "
      style="width: 404px; height: 110px; align-self: center">
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
      tasks: [
        {
          title: 'chores',
          done: false
        },
        {
          title: 'home task',
          done: false
        }
      ]
    }
  },

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
