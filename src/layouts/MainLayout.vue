<template>
  <q-layout view="lHh Lpr lFf" class="bg-pink-2" >
    <q-header elevated class="bg-pink-8">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <div class="row justify-center items-baseline">
          <div class="text-h4 text-weight-bol text-uppercase text-pink-1 q-mx-md">
          My Todo List
        </div>
        <div class="text-subtitle">{{todayDate}}</div>
        </div>
        
      </q-toolbar>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
        class="bg-pink-3"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item to="/" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="description" class="text-pink-8"/>
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>

            <q-item to="/help" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="accessibility" class="text-pink-8"/>
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>

            <q-item to="/about" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="face" class="text-pink-8"/>
              </q-item-section>

              <q-item-section>
                About us
              </q-item-section>
            </q-item>

            <q-item to="/contacts" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="call" class="text-pink-8" />
              </q-item-section>

              <q-item-section>
                Contacts
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top bg-pink-10"  style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="70px" class="q-mb-sm">
              <img src="~assets/cat.jpg">
            </q-avatar>
            <div class="text-weight-bold text-pink-1">Nigina Gafurova</div>
            <div class="text-pink-1">@nininigina</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </q-page-container>

  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'

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
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  },
  computed:{
    todayDate(){
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'DD MMM YYYY')
    }
  }
})
</script>
