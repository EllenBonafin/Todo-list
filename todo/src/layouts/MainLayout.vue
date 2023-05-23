<template>
  <q-layout view="lHh Lpr lFf">
  <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
      <div class ="text-h3"> Todo</div>
      <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img src="https://cdn.pixabay.com/photo/2023/05/07/20/44/woman-7977101_1280.jpg" class="header-image absolute-top"/>
  </q-header>

  <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="300"
      >
        <q-scroll-area style="height: calc(100% - 188px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list"/>
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.pixabay.com/photo/2023/05/07/20/44/woman-7977101_1280.jpg" style="height: 165px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://www.petlove.com.br/images/breeds/193223/profile/original/golden_retriever-p.jpg?1532539102">
            </q-avatar>
            <div class="text-weight-bold">Ellen Carine Bonafin Marques </div>
            <div>@ellencarine@outklock</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>



<script>

import { computed, defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

import { date } from 'quasar'
export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = false
      }
}
  },
  computed:{
    todaysDate(){
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM')
    }
}
})
// export default {

</script>

<style lang="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter:grayscale(100%);
  }
</style>
