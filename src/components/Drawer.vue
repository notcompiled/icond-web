<template>
  <v-card
    height="900"
    width="250"
  >
    <v-navigation-drawer app left>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Application
          </v-list-item-title>
          <v-list-item-subtitle>
            subtext
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
      >
        <v-list-item 
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content :to="item.link">
            <v-list-item-title >{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-card>
</template>
<script>
  export default {
      name: "Drawer",
    data () {
      return {
        items: [
          { title: 'Registrar', icon: 'mdi-plus', link: '/login'},
          { title: 'Administrar Pagamentos', icon: 'mdi-cash', link: "/" },
        ],
        right: null,
      }
    },
  }
</script>
<style scoped>
.drwr{
display: flex;
flex-direction: column;
align-items: flex-start;
padding: 0px;

position: absolute;
width: 367px;
height: 960px;
left: 0px;
top: 64px;

background: #FFFFFF;
/* elevation/24 */

box-shadow: 0px 11px 15px rgba(0, 0, 0, 0.2);
}
