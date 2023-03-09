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

    <vNavbar v-bind:navbar_data="leftDrawerOpen"/>

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
import vNavbar from 'components/Navbar.vue'
import { date } from 'quasar'

export default defineComponent({
  name: 'MainLayout',

  components: {
    vNavbar
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
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
