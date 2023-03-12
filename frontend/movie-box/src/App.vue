<template>
  <v-app class="application">
    <v-app-bar
        color="black"
        prominent
    >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>Movie Box</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn variant="text" icon="mdi-magnify"></v-btn>
        <v-btn variant="text" icon="mdi-filter"></v-btn>
        <v-btn variant="text" icon="mdi-dots-vertical"></v-btn>
    </v-app-bar>
    <v-navigation-drawer
        v-model="drawer"
        location="bottom"
        temporary
      >
        <v-list
          density="compact"
          nav
        >
          <v-list-item prepend-icon="mdi-view-dashboard" title="Home" to="/" value="home"></v-list-item>
          <v-list-item prepend-icon="mdi-forum" title="About" to="/about" value="about"></v-list-item>
        </v-list>
    </v-navigation-drawer>
    <v-main>
      <router-view/>
    </v-main>
    <v-footer class="footer d-flex flex-column">
      <div class="px-4 py-2 text-center w-100">
        {{ new Date().getFullYear() }}
        <div class="stack">
          <p>Backend - Java Spring Boot</p>
          <p>Frontend - Vue</p>
          <p>Database - MongoDB</p>
        </div>
      </div>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
      drawer: false,
      group: null,
      items: [
        {
          title: 'Home',
          loc: '/',
        },
        {
          title: 'About',
          loc: 'about',
        }
      ],
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  watch: {
    group () {
      this.drawer = false
    },
  },
}
</script>

<style scoped>

.application {
  background-color: #242424;
}
.footer{
  background-color: #000000;
  color: white;
  position:fixed;
  bottom:0;
  width: 100%;
}

.stack {
  text-align: left;
  font-size: 10px;
}
</style>