<template>
    <div>
    <v-app-bar
        color="primary"
        prominent
    >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>My files</v-toolbar-title>

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

      
    </div>
</template>

<script>
  export default {
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
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>