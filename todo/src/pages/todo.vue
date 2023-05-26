<template>

<q-page class="bg-grey-3 column">
  <div class="row q-pa-sm bg-primary">
  New task
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
  </q-page>
</template>

<script>
import {defineComponent} from 'vue'
export default defineComponent({
      data(){
        return{
          tasks:[
            {
              title: 'read the book',
              done: true
            },
            {
              title: 'sing with your mom',
              done: false
            },
            {
              title: 'dance with your dad',
              done: false
            }
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

        }
      }
  }
)
//
</script>

<style lang="scss">
  .done{
    .q-item__label{
      text-decoration: line-through;
      color: #bbb;
    }
  }
</style>

