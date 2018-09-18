<template>
  <v-layout align-center justify-center container >
          <v-flex xs12 sm10 md6 >
            <v-card class="elevation-12">
              <v-toolbar dark color="blue">
                <v-toolbar-title>Multiple Choice</v-toolbar-title>
              </v-toolbar>
              <div class="v-card__text"> 
                <v-list two-line v-for="(input, index) in inputs" :key="index">
                  <div class="layout align-center ">
                  <v-flex xs2 sm1 >
                    <v-checkbox @change="handleChange($event, index)" v-model="input.one"></v-checkbox>
                  </v-flex>
                  <v-flex xs8 sm10 >
                    <v-text-field v-model="input.two" color="blue darken-2" label="Add Choice"></v-text-field>
                  </v-flex>
                  <v-flex xs2 sm1 >
                    <v-btn class="v-btn--icon" color="error" @click="deleteRow(index)"><v-icon >delete</v-icon></v-btn>
                  </v-flex>
                 </div>
                  
                </v-list>
                <v-spacer></v-spacer>
                <v-card-actions class="pl-0">
                  <v-btn @click="addRow">Add row</v-btn>
                </v-card-actions>

                <router-link class="pr-0" :to="{ name: 'about', params: { listedUsersData: selected } }">List selected</router-link>
              
              </div>
            </v-card>
          </v-flex>
  </v-layout>
</template>

<script>
import Vue from 'vue'
import {mapState} from 'vuex';

export default {
  name: 'Add custom fields',
  data: function () {
        return {
          inputs: [{ one: false, two: 'default'}],
          selected: []
        }
  },
  computed: mapState({
    custom: 'title'
  }),
  methods : {
    handleChange: function (isChecked, index) {
      this.setSelected();
    },
    setSelected: function() {
      this.selected = this.inputs.filter(x => x.one == true);
    },
    addRow: function () {
      this.inputs.push({
        one: '',
        two: 'default'
      })
    },
    deleteRow(index) {
      this.inputs.splice(index,1)/
      this.setSelected();
    }
  }
}
</script>
