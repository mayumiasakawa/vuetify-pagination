<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title>
        <span>Vuetify Pagination</span>
      </v-toolbar-title>
    </v-app-bar>
    <v-content>
      <div class="text-center">
        <v-list>
          <v-list-item v-for="list in displayLists" :key="list.index">
            <v-list-item-content>
              <v-list-item-title>{{ list.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
        <v-pagination
        v-model="page"
        :length="length"
        @input ="pageChange"
        >
        </v-pagination>
      </div>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      page: 1,
      length: 0,
      lists: [],
      displayLists: [],
      pageSize: 10,
    }
  },
  methods: {
  pageChange: function(pageNumber){
    this.displayLists = this.lists.slice(this.pageSize*(pageNumber -1), this.pageSize*(pageNumber));
  }, 
},
  mounted: function(){
    this.lists= new Array(99).fill().map((v,i)=> {
      return { id : i,title : 'Title' + i};
    });
    this.length = Math.ceil(this.lists.length/this.pageSize);
    this.displayLists = this.lists.slice(this.pageSize*(this.page -1), this.pageSize*(this.page));
  }
};
</script>
