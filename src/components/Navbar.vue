<template>
  <v-app-bar app color="#3853D8" dark>
    <div>
    <v-menu offset-y :close-on-content-click="false">
      <template v-slot:activator="{ on, attrs }">
        <v-btn icon v-bind="attrs" v-on="on">
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item>
          <v-text-field
            v-model="searchQuery"
            label="Search"
            append-icon="mdi-magnify"
            @click:append="search"
          ></v-text-field>
        </v-list-item>
      </v-list>
    </v-menu>
 </div>
    <v-divider vertical class="ml-1 mr-3"></v-divider>
    <v-btn icon @click="menuOpen = !menuOpen">
      <v-icon>mdi-menu</v-icon>
    </v-btn>
      <v-menu v-model="menuOpen" :nudge-width="200" offset-x :position-x="x" :position-y="y">
      <v-list>
        <v-list-item v-for="(item, index) in items" :key="index">
          <v-list-item-title> {{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    <v-toolbar-title>
      <span class="caption"></span>
    </v-toolbar-title>
    <v-divoder vertical class="ml-5"></v-divoder>
    <div style="position:absolute; margin-left:auto; margin-right: auto; left:0; right:0; text-align: center;">
    <h4>Idea Project</h4>
    </div>
    <v-spacer></v-spacer>
    <v-divider vertical></v-divider>
    <v-btn icon class="mx-1">
      <v-icon>mdi-account-outline</v-icon>
    </v-btn>
    <v-divider vertical></v-divider>
    <v-btn icon class="mx-1">
      <v-badge color="#94D0EF" content="2">
        <v-icon>mdi-cart-outline</v-icon>
      </v-badge>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      menuOpen: false,
      items: [
        { title: 'Home' }, 
        { title: 'About' },
        { title: 'Contact' } 
        ],
        x: 0,
        y: 0,
        searchQuery: "",
  }
  },
  methods: {
    onResize () {
      this.x = window.innerWidth > 600 ? 'right' : 'center';
      this.y = window.innerHeight > 800 ? 'top' : 'bottom';
      },
      search() {
      // Perform your search logic here
      console.log("Searching for:", this.searchQuery);
    },
  }
}
</script>

<style>
.v-toolbar__title{
  font-size: 1rem !important;
}

.v-badge__badge{
  font-size: 10px !important;
  height: 18px !important;
  min-width: 18px !important;
}

.menu  {
  background-color: #333;
  padding: 10px;
  top: 48px;
  left: 83px;
}

.v-menu__content {
      /* Add your custom styles here */
      background-color: #f5f5f5;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
</style>