<template>
  <v-app> 
    <v-app-bar app color="info" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>Notepat App</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text>
        <span> Login </span>
        <v-icon right>mdi-login-variant</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
       <router-view />
    </v-main>

    <!-- End Footer -->
    <v-footer dark padless>
      <v-col cols="12">
        <v-card flat tile class="lighten-1 white--text text-center">
          <v-card-text>
            <v-btn href="https://www.facebook.com/carliitos.3098/" class="mx-4 white--text" target="_blank" icon>
              <v-icon size="20px"> mdi-facebook </v-icon>
            </v-btn>
            <v-btn href="https://github.com/Carlosramirez-dev" class="mx-4 white--text" target="_blank" icon>
              <v-icon size="20px"> mdi-github </v-icon>
            </v-btn>
            <v-btn href="" class="mx-4 white--text" target="_blank" icon>
              <v-icon size="20px"> mdi-linkedin </v-icon>
            </v-btn>
            <v-btn href="https://www.instagram.com/carlosr.dev" class="mx-4 white--text" target="_blank" icon>
              <v-icon size="20px"> mdi-instagram </v-icon>
            </v-btn>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-text class="white--text">
            {{ new Date().getFullYear() }} — <strong>Carlos Ramirez</strong>
          </v-card-text>
        </v-card>
      </v-col>
  </v-footer>
<!-- End Footer -->
  
  <v-navigation-drawer v-model="drawer" absolute temporary dark>
    <v-list-item>
      <v-list-item-avatar>
        <v-img src="https://lh3.googleusercontent.com/ogw/ADGmqu_3aK6hSKAMk6RIxxYc8T9RQUwGza9OOowKOSfWVA=s83-c-mo"></v-img>
      </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title >Carlos Ramirez</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>
      <v-list dense>
        <v-list-item v-for="item in items" :key="item.title" :to="item.name">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
   
  },

  data: () => ({
    drawer: null,
    items: [
      { title: 'Home', icon: 'mdi-view-dashboard', name: '/' },
      { title: 'About', icon: 'mdi-forum', name: 'about' },
    ],
  }),
};
</script>
