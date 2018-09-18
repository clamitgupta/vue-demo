<template>
  <v-layout align-center justify-center container >
          <v-flex xs12 sm10 md6 >
            <v-card class="elevation-12">
              <v-toolbar dark color="blue">
                <v-toolbar-title>Selected values</v-toolbar-title>
              </v-toolbar>
              <div class="v-card__text"> 
                <v-list two-line v-for="(input, index) in listedUsersData" :key="index">
                  <v-list-tile-content>
                    <v-list-tile-title v-html="index+' - '+input.two"></v-list-tile-title>
                 </v-list-tile-content>
                </v-list>
                <v-list v-if="!listedUsersData.length">
                  <v-list-tile-title v-html="'No selected value found'"></v-list-tile-title>
                </v-list>
                <v-spacer></v-spacer>
              </div>
            </v-card>
          </v-flex>
  </v-layout>
</template>

<script>
import {mapState} from 'vuex';

export default {
  name: 'Add custom fields',
  data: function () {
        return {
          listedUsersData: []
        }
  },
  created() {
      this.listedUsersData = this.$route.params.listedUsersData;
  },
  computed: mapState({
    custom: 'title'
  }),
  methods : {
  }
}
</script>
