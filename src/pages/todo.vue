<template>

<q-page class="bg-grey-3 column">
  <div class="row q-pa-sm bg-primary">
    <q-input
    v-model="newTask"
    class="col"
    @keyup.enter="addTask"
    square
    filled
    bg-color="wihte"
    placeholder="Add task"
    dense>

        <template v-slot:append>
          <q-btn
          @click="addTask"
          round
          dense
          flat icon="add" />
        </template>
      </q-input>
  </div>
  <q-list class="bg-white" separator bordered>
      <q-item v-for="(task, index) in tasks"
      :key="task.title"
      @click="task.done = !task.done"
      :class="{ 'done bg-green-1' : task.done}"
      clickable
      v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done"
          class="no-pointer-events"
          color="primary"/>
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>

        <q-item-
        v-if="task.done"
        side>
        <q-btn
        @click.stop="deleteTask(index)"
        flat
        round
        dense
        color="primary" icon="delete" />
        </q-item->
      </q-item>
    </q-list>
    <div class="no-task absolute-center">
      <div class="text-h6 text-primary text-center">
        No tasks yet
      </div>
    </div>
  </q-page>
</template>

<script>
import {defineComponent} from 'vue'
export default defineComponent({
      data(){
        return{
          newTask: '',
          tasks:[
          //   {
          //     title: 'read the book',
          //     done: true
          //   },
          //   {
          //     title: 'sing with your mom',
          //     done: false
          //   },
          //   {
          //     title: 'dance with your dad',
          //     done: false
          //   }
          ]
        }
      },
      methods:{
        deleteTask(index){
        this.$q.dialog({
        dark: true,
        title: 'Confirm',
        message: 'Would you like delete this task?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index, 1)
        this.$q.notify("Task deleted :)")
      })

        },
        addTask(){
        this.tasks.push({
          title: this.newTask,
          done: false
        })
      }
      }


  }
)
//
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Merienda&display=swap');
  .done{
    .q-item__label{
      text-decoration: line-through;
      color: #bbb;
    }
  }
  .no-task{
    opacity: 0.5;
  }
</style>

