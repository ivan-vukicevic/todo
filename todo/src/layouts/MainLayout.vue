<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-xl">
        <div class="text-h3">Lista obaveza</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img src="../statics/sunnyHome.jpg" class="header-image absolute-top" />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      
      show-if-above
      :mini="miniState"
      @mouseover="miniState = false"
      @mouseout="miniState = true"
      mini-to-overlay
      :width="200"
      :breakpoint="500"
      bordered
      content-class="bg-grey-3 bg-blue-10"
    >
      <q-scroll-area class="fit ">
        <q-list padding>
          <q-item clickable v-ripple to="/">
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section >
              Lista obaveza
            </q-item-section>
          </q-item>

          <q-item active clickable v-ripple to="/help">
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section>
              Opis
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";
import { date } from "quasar";

const linksData = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev"
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework"
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev"
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev"
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev"
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev"
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev"
  }
];

export default {
  name: "MainLayout",
  components: { EssentialLink },
  data() {
    return {
      leftDrawerOpen: false,
      miniState: true,
      essentialLinks: linksData
    };
  },

  computed: {
    todaysDate() {
      let timeStamp = Date.now();
      let day = null;
      if (date.formatDate(timeStamp, "d") == 1) {
        day = "Ponedeljak ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 2) {
        day = "Utorak ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 3) {
        day = "Srijeda ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 4) {
        day = "Četvrtak ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 5) {
        day = "Petak ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 6) {
        day = "Subota ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
      if (date.formatDate(timeStamp, "d") == 7) {
        day = "Nedelja ";
        return day + date.formatDate(timeStamp, "D MMM");
      }
    }
  }
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.33;
  filter: grayscale(10%);
}
</style>
