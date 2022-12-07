<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="las la-bars"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          YNBO
        </q-toolbar-title>

        <div>Red Social Open Source</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Nosotros',
    icon: 'las la-people-carry',
    link: 'https://quasar.dev'
  },
  
  {
    title: 'Políticas',
    icon: 'las la-landmark',
    link: 'https://quasar.dev'
  },
  
  {
    title: 'Privacidad',
    icon: 'las la-user-shield',
    link: 'https://quasar.dev'
  },
  
 

  {
    title: 'Facebook',
    caption: '@YovanYauneEnovore',
    icon: 'lab la-facebook-f',
    link: 'https://facebook.quasar.dev'
  },
  
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
  }
})
</script>
