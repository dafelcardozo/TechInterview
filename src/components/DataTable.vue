<template>
  <v-container>
    <v-row>
        <v-card>
            <v-card-title>
                Data Table
            </v-card-title>
              <v-data-table :items="persons" :headers="headers">
                <template v-slot:item.avatar="{ item }">
                  <div class="p-2">
                    <v-img :src="item.avatar" :alt="item.name" height="60px" width="50px"></v-img>
                  </div>
                </template>
            </v-data-table>

            <!-- v-card-subtitle><p>Uh oh. There is nothing there. Using the data at <a href="https://random-data-api.com/">https://random-data-api.com/</a>, populate the table
      below with headers and make it searchable. Also, expand the table to full width of the container. Let Bob know when complete.</p></v-card-subtitle -->
          
    </v-card>
    </v-row>
    <v-row>
      <p>adasd</p>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
 
  data () {
    return {
      persons: [],
      headers: [
        { text: "Name", align: "start", sortable: true, value: "first_name" },
        { text: "Last name",  sortable: true, value: "last_name" },
        {text: "Avatar", sortable:false, value:"avatar"}
      ],
    }
  },
  filters: {
  },
  async mounted () {
    const {data}  = await axios.get('https://random-data-api.com/api/v2/users?size=10');
    this.persons = data;    
  }
};
</script>
