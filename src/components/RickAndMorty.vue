<template>
  <v-container>
<v-row>Total de Personajes: {{info.count}}. </v-row>

    <v-row>
      <v-col cols="3" v-for="character in characters">
        <v-card>
          <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title>{{character.name}}</v-card-title>
                <v-card-subtitle>
                  <v-chip
                    :color="character.status ? 'green' : (character.status === false ? 'red' : 'gray')"
                    :text="character.status ? 'Alive' : (character.status === false ? 'Dead' : 'Unknown')"
                    class="text-uppercase"
                    label
                    size="small"
                  ></v-chip>
                </v-card-subtitle>
                <v-card-text>
                  Last Location: {{ character.location.name }}
                </v-card-text>
              </div>
              <v-avatar
                class="ma-3"
                size="128"
                rounded="0"
              >
                <v-img :src="character.image"></v-img>
              </v-avatar>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>


  <script>
import axios from 'axios'
export default {
  data () {
    return {
      characters: [], 
      info:[],
    }
  },
  mounted () {
  axios
    .get('https://rickandmortyapi.com/api/character')
    .then(response => {
      this.characters = response.data.results,
      this.info=response.data.info
          })
    .catch(error => {
      console.log(error)
    })
  }
}
  </script> 
  
  