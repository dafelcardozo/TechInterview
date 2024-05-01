<template>
  <v-container fluid fill-height>
  <v-layout child-flex>
        <v-card>
          <v-text-field
        v-model="search"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        variant="outlined"
        hide-details
        single-line
      ></v-text-field>
            <v-card-title>
              People I used to know...
            </v-card-title>
              <v-data-table :items="persons" :headers="headers" :search="search" >
                <template v-slot:item.avatar="{ item }">
                  <div class="p-2">
                    <v-img :src="item.avatar" :alt="item.name" height="60px" width="50px"></v-img>
                  </div>
                </template>
                <template v-slot:item.address="{ item }">
                  <div class="p-2">
                    {{ item.address.city }}, {{ item.address.country }}
                  </div>
                </template>
            </v-data-table>

            <!-- v-card-subtitle><p>Uh oh. There is nothing there. Using the data at <a href="https://random-data-api.com/">https://random-data-api.com/</a>, populate the table
      below with headers and make it searchable. Also, expand the table to full width of the container. Let Bob know when complete.</p></v-card-subtitle -->
          
    </v-card>
  </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
 
  data () {
    return {
      persons: [],
      headers: [
        {text: "Avatar", sortable:false, value:"avatar"},
        { text: "Name", align: "start", sortable: true, value: "first_name" },
        { text: "Last name",  sortable: true, value: "last_name" },
        { text: "Email",  sortable: true, value: "email" },    
        {text:"Location", sortable:false, value:"address"}
      ],
      search: ""
    }
  },
  filters: {
  },
  async mounted () {
    const {data}  = await axios.get('https://random-data-api.com/api/v2/users?size=10');
    console.info(data);
    this.persons = data;    
  }
};
</script>
