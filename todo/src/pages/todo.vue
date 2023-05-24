<template>
  <q-page class="bg-grey-3 column">
    <q-list class="bg-white">
      <q-item
      v-for="task in tasks"
      :key="task.title"
       v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="color" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
      </q-item>

    </q-list>
  </q-page>
</template>

<script>

export default({
      data(){
        return{
          tasks:[
            {
              title: 'read the book',
              done: false
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
      }
})
</script>
