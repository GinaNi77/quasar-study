<template>
 
    <q-page class="flex column flex-center">
       
        <transition name="fade">
            <div v-if="showP" class="text-h4 text-center q-my-md text-pink-10">Contacts</div>    
        </transition> 
        <div class="flex column flex-center">
            <img src="~assets/cat.jpg" alt="" class="q-mb-md"> 
            <q-btn color="deep-orange" glossy label="Kitty" @click="showP=!showP" />
        </div>  
    
    </q-page>

</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
    setup() {
        const showP = ref(false)

        return {
            showP
        }
    },
  
})
</script>


<style scoped>
.fade-enter-from{
    opacity: 0;
}
.fade-enter-to{
    opacity: 1;
}
.fade-enter-active{
    transition: all 2s ease;
}
.fade-leave-from{
    opacity: 1;
}
.fade-leave-to{
    opacity: 0;
}
.fade-leave-active{
    transition: all 2s ease;
}
</style>


