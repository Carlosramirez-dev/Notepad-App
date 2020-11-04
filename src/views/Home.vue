<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="6">
        <v-card 
         class="mx-auto"
         max-width="400"
        >
          <v-img 
            lass="white--text align-end"
            height="200px"
            src="https://cdn.pixabay.com/photo/2016/08/09/21/54/yellowstone-national-park-1581879_960_720.jpg" 
          >
          </v-img>
          <v-card-title>Top 10 Australian beaches</v-card-title>
           <v-card-text class="text--primary">
              <div>Whitehaven Beach</div>
              <div>Whitsunday Island, Whitsunday Islands</div>
           </v-card-text>
          <v-card-actions>
            <v-btn color="orange" text @click="dialog = true"> Share </v-btn>
            <v-btn color="orange" text> Explore </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" sm="6">
        <v-card
         class="mx-auto"
         max-width="400"
        >
          <v-img 
            lass="white--text align-end"
            height="200px"
            src="https://cdn.pixabay.com/photo/2019/04/25/16/01/jetty-4155214_960_720.jpg"
          >
          </v-img>
          <v-card-title>Top 10 Australian beaches</v-card-title>
           <v-card-text class="text--primary">
              <div>Whitehaven Beach</div>
              <div>Whitsunday Island, Whitsunday Islands</div>
           </v-card-text>
          <v-card-actions>
            <v-btn color="orange" text @click="dialog = true"> Share </v-btn>
            <v-btn color="orange" text> Explore </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" sm="6">
        <v-card
         class="mx-auto"
         max-width="400"
        >
          <v-img 
            lass="white--text align-end"
            height="200px"
            src="https://cdn.pixabay.com/photo/2015/12/29/14/51/landscape-1112911_960_720.jpg"
          >
          </v-img>
          <v-card-title>Top 10 Australian beaches</v-card-title>
           <v-card-text class="text--primary">
              <div>Whitehaven Beach</div>
              <div>Whitsunday Island, Whitsunday Islands</div>
           </v-card-text>
          <v-card-actions>
            <v-btn color="orange" text @click="dialog = true"> Share </v-btn>
            <v-btn color="orange" text> Explore </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col cols="12" sm="6">
        <v-card
         class="mx-auto"
         max-width="400"
        >
          <v-img 
            lass="white--text align-end"
            height="200px"
            src="https://cdn.pixabay.com/photo/2020/06/18/11/27/landscape-5313115_960_720.jpg"
          >
          </v-img>
          <v-card-title>Top 10 Australian beaches</v-card-title>
           <v-card-text class="text--primary">
              <div>Whitehaven Beach</div>
              <div>Whitsunday Island, Whitsunday Islands</div>
           </v-card-text>
          <v-card-actions>
            <v-btn color="orange" text @click="dialog = true"> Share </v-btn>
            <v-btn color="orange" text> Explore </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <!-- Dialog -->
    <v-dialog v-model="dialog" width="500" persistent>
      <v-card>
        <v-card-title>Este es el titulo</v-card-title>
        <v-card-text>Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
        Saepe odio autem natus asperiores dicta eius libero dolore laborum fuga neque placeat dolores,
        necessitatibus impedit cumque explicabo voluptas facilis nihil aliquam.</v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue" text @click="dialog = false">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!-- Fin Dialog -->
  </v-container>
</template>

<script>
export default {
  name: 'Home',
  components: {
   //
  },
  data() {
    return {
      dialog: false
    }
  },
}
</script>
