<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        

        <q-toolbar-title>
          Aplicacion de Camara
        </q-toolbar-title>

        
      </q-toolbar>
    </q-header>

<q-footer elevated>
        
           <q-tabs >
        
        
        <q-route-tab to="/" name="Home" icon="home" label="Home" />
        <q-route-tab to="camera" name="photos" icon="photo" label="Photos" />
        
       
      </q-tabs>
        
      </q-footer>

    <q-page-container class="bg-grey-5">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>


const linksData = [
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
];

export default {
  name: 'MainLayout',
  
  data () {
    return {
      
    }
  }
}
</script>
