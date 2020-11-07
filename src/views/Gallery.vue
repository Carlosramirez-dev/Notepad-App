<template>
    <v-container>
    <v-row>
      <v-col cols="12" sm="6" md="6" v-if="formAgregar"> 
        <v-card 
         class="mx-auto mb-3 pa-3"
         max-width="500"
        >
        <h2>
          Agregar nueva visita
        </h2>
          <v-form @submit.prevent="addPlace">
            <v-text-field label="Nombre del lugar" v-model="titulo"></v-text-field>
            <v-textarea label="Descripción del lugar" rows="2" v-model="descripcion"></v-textarea>
            <v-text-field label="Imagen del lugar (url)" v-model="image"></v-text-field>
            <v-card-actions>
              <v-btn color="success" type="submit" block> Agregar Visita </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-col>

      <v-col cols="12" sm="6" md="6" v-if="!formAgregar"> 
        <v-card 
         class="mx-auto mb-3 pa-3"
         max-width="500"
        >
        <h2>
          Editar visita
        </h2>
          <v-form @submit.prevent="editPlace">
            <v-text-field label="Nombre del lugar" v-model="titulo"></v-text-field>
            <v-textarea label="Descripción del lugar" rows="2" v-model="descripcion"></v-textarea>
            <v-text-field label="Imagen del lugar (url)" v-model="image"></v-text-field>
            <v-card-actions>
              <v-btn color="warning" type="submit" block> Editar Visita </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-col>

      <v-col cols="12" sm="6" md="6">
        <v-card
         class="mx-auto mb-3"
         max-width="500"
         v-for="(item, index) in listPlaces" :key="index"
        >
          <v-img 
            lass="white--text align-end"
            height="200px"
            v-bind:src="item.image"
          >
          </v-img>
          <v-card-title>{{ item.titulo}}</v-card-title>
           <v-card-text class="text--primary">              
              <div> {{ item.descripcion }}</div>
           </v-card-text>
          <v-card-actions>
            <v-btn color="warning" text @click="edit(index)"> <v-icon left dark > mdi-pencil </v-icon> Edit </v-btn>
            <v-btn color="error" text @click="deletePlace(index)"> <v-icon left dark > mdi-delete </v-icon> Delete </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>

    <!-- Snackbar -->
    <v-snackbar
      v-model="snackbar"
      :color="pintar"
      type="error"
    >
     <v-icon
        left
        color="white"
      >
        {{ icon }}
      </v-icon>
      {{ mensaje }}

      <template v-slot:action="{ attrs }">
        <v-btn
          color="white"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
    <!-- End Snackbar -->
  </v-container>
</template>

<script>
/**
 * @copyright carlosramirezdev@gmail.com todos los derechos reservados
 * @author carlosr.dev
 * @description CRUD de registro de visitas
 */

export default {
  name: 'Gallery',
  components: {
   //
  },
  data() {
    return {
      listPlaces: [
        {
          id: 1, 
          titulo: 'Top 10 Australian beaches', 
          descripcion: 'Whitehaven Beach, Whitsunday Island, Whitsunday Islands', 
          image: 'https://cdn.pixabay.com/photo/2019/04/25/16/01/jetty-4155214_960_720.jpg'
        },
        {
          id: 2, 
          titulo: 'Top 10 Australian beaches', 
          descripcion: 'Whitehaven Beach, Whitsunday Island, Whitsunday Islands', 
          image: 'https://cdn.pixabay.com/photo/2016/08/09/21/54/yellowstone-national-park-1581879_960_720.jpg'
        },
      ],
      titulo: '',
      descripcion: '',
      image: '',
      snackbar: false,
      mensaje: '',
      pintar: '',
      icon: '',
      formAgregar: true,
      indexPlace: ''
    }
  },
  methods: {
    addPlace(){
      if(this.titulo === '' || this.descripcion === '' || this.image === '') {
            this.pintar = 'error'
            this.snackbar = true
            this.mensaje = 'Llena todos los campos!'
            this.icon = 'mdi-cancel'
      }else{
        this.listPlaces.push({
          id: Date.now(),
          titulo: this.titulo,
          descripcion: this.descripcion,
          image: this.image
        })
         this.titulo = '',
         this.descripcion = '',
         this.image = '',
         this.pintar = 'success'
         this.icon = 'mdi-checkbox-marked-circle'
         this.snackbar = true
         this.mensaje = 'Visita Agregada!'
         localStorage.setItem('places-vue', JSON.stringify(this.listPlaces));
      }
    },

    deletePlace(index){
      this.listPlaces.splice(index, 1);
      localStorage.setItem('places-vue', JSON.stringify(this.listPlaces));
      this.pintar = 'error'
      this.icon = 'mdi-delete'
      this.snackbar = true
      this.mensaje = 'Visita Eliminada!'
    },

    edit(index){
      this.formAgregar = false
      this.titulo = this.listPlaces[index].titulo
      this.descripcion = this.listPlaces[index].descripcion
      this.image = this.listPlaces[index].image
      this.indexPlace = index
    },

    editPlace(){
      this.listPlaces[this.indexPlace].titulo = this.titulo
      this.listPlaces[this.indexPlace].descripcion = this.descripcion
      this.listPlaces[this.indexPlace].image = this.image
      localStorage.setItem('places-vue', JSON.stringify(this.listPlaces));
      this.titulo = '',
      this.descripcion = '',
      this.image = '',
      this.pintar = 'orange'
      this.snackbar = true
      this.mensaje = 'Editaste la visita!'
      this.icon = 'mdi-pencil'
      this.formAgregar = true
    }
  },
    created: function(){
        let dataDB = JSON.parse(localStorage.getItem('places-vue'));
        if (dataDB === null) {
            this.listPlaces = [];
        }else{
            this.listPlaces = dataDB;
        }
    }
}
</script>
