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
        tag="label"
        v-ripple
        v-for="task in tasks" :key="task.title">
        <q-item-section avatar>
          <q-checkbox v-model="task.done" val="teal" color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
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
  }
}

</script>
