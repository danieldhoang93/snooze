<template>
  <q-layout view="lHr Lpr lFf">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title>
          Snooze
        </q-toolbar-title>

        <q-btn
          flat
          dense
          round
          icon="settings"
          aria-label="Menu"
          @click="rightDrawerOpen = !rightDrawerOpen"
        />
      </q-toolbar>
    </q-header>
    <q-drawer
      v-model="rightDrawerOpen"
      side="right"
      overlay
      :width="320"
      class="rightDrawer">
        <q-list dark>
          <div class="navPadding">
            <q-btn
            class=" absolute-top-right iconPadding smallWindow"
            flat
            dense
            round
            icon="settings"
            aria-label="Menu"
            @click="rightDrawerOpen = !rightDrawerOpen"/>
          </div>
        
        <q-item
          v-for="link in settingsLinks"
          :key="link.title"
          class="navFont text-weight-thin shadow2"
          clickable
          v-ripple>
            <q-item-section class="q-pa-sm">
              <q-item-label class="text-subtitle1">{{ link.title }}</q-item-label>
              <q-item-label class="text-body2">{{ link.caption }}</q-item-label>
            </q-item-section>
          </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      rightDrawerOpen: false,
      settingsLinks: [
        {
          title: 'Charity',
          caption: 'Human Rights Watch',
          icon: 'home',
          link: '/'
        },
        {
          title: 'Payment Method',
          caption: 'Checking•••5555 ',
          icon: 'login',
          link: '/login'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.q-drawer {
  background:rgb(14, 14, 14);
  border-left:2px solid #1D1D1D;
}

.iconPadding {
    margin-top:7px;
    margin-right:12px;
}

.q-btn.smallWindow {
      display:all;
    }

.navPadding {
      padding: 2em;
    }

</style>
