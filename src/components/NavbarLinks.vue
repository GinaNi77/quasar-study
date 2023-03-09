<template>
            <q-item :to="navbarLink_data.link" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon :name="navbarLink_data.icon" class="text-pink-8"/>
              </q-item-section>

              <q-item-section>
                {{navbarLink_data.title}}
              </q-item-section>
            </q-item>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: "v-navbar-links",

    props: {
        navbarLink_data:{
            type: Object,
            default() {
                return {}
            }
        }
    },
    setup() { },
})
</script>
