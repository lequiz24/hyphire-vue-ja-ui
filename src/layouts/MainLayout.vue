<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="header">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Robinson's App </q-toolbar-title>

        <div><br /></div>

        <!-- DROP DOWN WITH FADE IN FADE OUT EFFECT -->

        <q-btn color="yellow" label="MY PROJECTS" text-color="black">
          <q-menu transition-show="rotate" transition-hide="rotate">
            <q-list style="min-width: 100px">
              <q-item clickable>
                <q-item-section>NEW PROJECTS</q-item-section>
              </q-item>
              <q-item clickable>
                <q-item-section>PENDING PROJECTS</q-item-section>
              </q-item>
              <q-separator></q-separator>
              <q-item clickable>
                <q-item-section>COMPLETED PROJECTS</q-item-section>
              </q-item>
            </q-list>
          </q-menu>
        </q-btn>
      </q-toolbar>
    </q-header>
    <q-footer reveal elevated class="footer">
      <q-toolbar class="toolbar">
        <q-toolbar-title class="title">
          @KIPKEMOI ROBINSON. All Rights Reserved
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> My Account </q-item-label>

        <EssentialLink
          v-for="link in linksList"
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

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "My Profile",
    caption: "Personal Details",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github Account",
    caption: "github.com/Robinson",
    icon: "code",
    link: "https://github.com/lequiz24",
  },
  {
    title: "Linkedin Account",
    caption: "Robinson Kipkemoi",
    icon: "chat",
    link: "https://www.linkedin.com/in/robinson-kipkemoi-3a527a5a/",
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style scoped>
.header {
  background-color: #070707;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}
.footer {
  background-color: #070707;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
}

.toolbar {
  width: 100%;
}

.title {
  margin: 0;
}

@media (max-width: 360px) {
  .q-layout-header,
  .q-layout-footer {
    padding: 5px;
    font-size: 12px;
  }
}
</style>
