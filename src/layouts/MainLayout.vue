<template>
  <q-layout view="hHh LpR lff">
    <q-header elevated class="bg-grey-9 text-white">
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="menu"
          v-show="!leftDrawerOpen"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title class="q-py-sm">
          <q-btn @click="$router.push('/')" flat>
            <img
              style="width: 200px; max-width: 80vw"
              src="../assets/logo.png"
            />
          </q-btn>
        </q-toolbar-title>

        <div class="q-gutter-x-xs">
          <q-btn flat round dense icon="notifications" />
          <q-btn flat round dense icon="mode_comment" />
          <span>Hi, admin</span>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar.png" />
          </q-avatar>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      show-if-above
      :breakpoint="500"
      v-model="leftDrawerOpen"
      side="left"
      behavior="desktop"
      bordered
    >
      <q-list separator>
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
import EssentialLink from "../components/EssentialLink.vue";
import { useQuasar } from "quasar";
import { ref } from "vue";

export default {
  data() {
    return {
      leftDrawer: ref(false),
    };
  },

  components: {
    EssentialLink,
  },
  setup() {
    const $q = useQuasar();
    const linksList = [
      {
        title: "Overview",
        icon: "cloud_queue",
        link: "/",
        useMethod: "",
      },
      {
        title: "Report",
        icon: "description",
        link: "/",
        useMethod: "",
      },

      {
        title: "Map",
        icon: "map",
        link: "/",
        useMethod: "",
      },
      {
        title: "Location",
        icon: "explore",
        link: "/",
        useMethod: "",
      },
      {
        title: "Device Management",
        icon: "format_list_bulleted",
        link: "/",
        useMethod: "",
      },
      {
        title: "Manage Work",
        icon: "format_list_bulleted",
        link: "/",
        useMethod: "",
      },
      {
        title: "Setting",
        icon: "format_list_bulleted",
        link: "/",
        useMethod: "",
      },
    ];
    const leftDrawerOpen = ref(true);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
    $q.platform.is.mobile;
  },
};
</script>
