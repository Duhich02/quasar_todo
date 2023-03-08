<template>
  <q-page class="flex flex-center bg-black-3 column">
    <q-list>
      <q-item
        tag="label"
        v-ripple
        v-for="task in tasks" :key="task.title"
      >
        <q-item-section avatar>
          <q-checkbox v-model="color" val="teal" color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
      </q-item>
    </q-list>
    <img
      alt="logo"
      src="../assets/welcome.gif "
      style="width: 404px; height: 110px"
    >
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
