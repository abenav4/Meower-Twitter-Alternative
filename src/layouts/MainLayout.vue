<template>
  <q-layout view="lHr lpR fFf">

    <q-header bordered class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-weight-bold">
          <span class="gt-sm">meower</span>
          <q-icon 
            class = "q-pa-md lt-md"
            name="fas fa-cat" 
            size = "md"
            color = "white"
          />
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered :width="280">
      <q-icon 
        class = "q-pa-md"
        name="fas fa-cat" 
        size = "lg"
        color = "primary"
      />

      <q-list>
      <q-item clickable v-ripple exact
      to="/">
        <q-item-section avatar>
          <q-icon  name="fas fa-home" size = "sm"/>

        </q-item-section>

        <q-item-section class = "text-h6 text-weight-bold">home</q-item-section>
      </q-item>

      <q-item clickable v-ripple exact
      to="/about">
        <q-item-section avatar>
          <q-icon  name="fas fa-question" size = "sm"/>

        </q-item-section>

        <q-item-section class = "text-h6 text-weight-bold">about</q-item-section>
      </q-item>

      

      
    </q-list>

    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <!-- drawer content -->
        <div class="q-pa-md">
    <div class="q-gutter-y-md column" style="max-width: 300px">
      <q-input class = "q-ma-md" rounded outlined 
      placeholder = "search meower"
      dense>
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>

      <q-list padding separator>
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class= "text-grey">politics</q-item-label>
          <q-item-label class = "text-weight-bold">The Bourgeois party wins another election</q-item-label>
          <q-item-label caption>It appears their policies are tremendously popular among the working class.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>13 min ago</q-item-label>
        </q-item-section>
      </q-item>

      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class= "text-grey">technology</q-item-label>
          <q-item-label class = "text-weight-bold">Facebook rebrands to Meta to avoid controversy</q-item-label>
          <q-item-label caption>This effort has done wonders to deflect and disavow.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>37 min ago</q-item-label>
        </q-item-section>
      </q-item>
      
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class= "text-grey">wellness</q-item-label>
          <q-item-label class = "text-weight-bold">mindfulness practices developed by the global north take the global south by storm</q-item-label>
          <q-item-label caption>Some wonder why these practices were not adopted sooner!</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>45 min ago</q-item-label>
        </q-item-section>
      </q-item>
      </q-list>
    </div>
  </div>
  
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },

      rightDrawerOpen,
      toggleRightDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      }
    }
  }
}
</script>