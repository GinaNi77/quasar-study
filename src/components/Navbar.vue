<template>
    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
        class="bg-pink-3"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>

            <vNavbarLinks
            v-for="navbarLink in navbarLinkList"
            :key="navbarLink.index"
            :navbarLink_data="navbarLink"/>

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
</template>

<script>
import { defineComponent, ref } from 'vue'
import vNavbarLinks from 'components/NavbarLinks.vue'

export default defineComponent({
    name: 'v-navbar',

    components: {
        vNavbarLinks
    },
     props: {
        
    },
    setup() {

        return{
            navbarLinkList:[
            {
                title: "Todo",
                icon: "description",
                link:"/",
            },
            {
                title: "Help",
                icon: "accessibility",
                link:"/help",
            },
            {
                title: "About us",
                icon: "face",
                link:"/about",
            },
            {
                title: "Contacts",
                icon: "call",
                link:"/contacts",
            },
            ],
        }
        
    },
})
</script>
