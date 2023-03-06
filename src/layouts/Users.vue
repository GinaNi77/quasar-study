<template>
    <!-- <q-layout>

         
    <div class="flex flex-center text-h2 text-weight-bold text-light-green-13 q-mb-md">
        Meow
           
    </div>
    
    <q-page-container>
        <router-view></router-view>
    </q-page-container>

    </q-layout> -->
    <q-layout view="hHh lpR fFf">

    <q-header class="bg-pink-10 text-white ">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Little meow-meow-header
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container class="flex items-center justify-center">
      <router-view />
    </q-page-container>

    <q-footer reveal class="bg-pink-12 text-white">
      <q-toolbar>
        <q-toolbar-title>
          
          <div>Little meow-meow-footer</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>