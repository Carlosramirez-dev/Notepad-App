<template>
  <v-app> 
    <v-app-bar app color="info" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>Notepad App</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text @click="dialog_login = true">
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
 <!-- navigation -->
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
  <!-- End navigation -->
    <!-- Dialog -->
  <v-row justify="center">
    <v-dialog
      v-model="dialog_login"
      persistent
      max-width="600px"
    >
      <v-card>
        <v-card-title>
          <span class="headline">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal first name*"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal middle name"
                  hint="example of helper text only on focus"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal last name*"
                  hint="example of persistent helper text"
                  persistent-hint
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Email*"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Password*"
                  type="password"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-select
                  :items="['0-17', '18-29', '30-54', '54+']"
                  label="Age*"
                  required
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-autocomplete
                  :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                  label="Interests"
                  multiple
                ></v-autocomplete>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog_login = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog_login = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
    <!-- Fin Dialog -->
  </v-app>
</template>

<script>
/**
 * @copyright carlosramirezdev@gmail.com todos los derechos reservados
 * @author carlosr.dev
 * @description Notepad App
 */

export default {
  name: 'App',

  components: {
   
  },

  data: () => ({
    drawer: null,
    dialog_login: false,
    items: [
      { title: 'Home', icon: 'mdi-home', name: '/' },
      { title: 'About', icon: 'mdi-forum', name: 'about' },
      { title: 'Gallery', icon: 'mdi-view-dashboard', name: 'gallery' },
    ],
  }),
};
</script>
