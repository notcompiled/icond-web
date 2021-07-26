<template>
  <div>
    <v-app>
  <v-navigation-drawer app class="drwr" left>
      <v-list-item>
        <v-list-item-content>
          
          <v-list-item-title class="text-dr">
            <v-icon size="150%"> mdi-account-box </v-icon>
            {{user.name}}
          </v-list-item-title>
          <v-list-item-subtitle class="text-dr-subtitle">
            {{user.function}}
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      

      <v-divider></v-divider>

      <v-list
      >
        <v-list-item 
          v-for="item in items"
          :key="item.title"
          :to="item.link"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title 
            class="text-dr-items">{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        
      </v-list>
      
    </v-navigation-drawer>

  <v-main>
    <v-container fluid fill-height class="background">

      <v-layout class="layout" align-center justify-space-between>

        <v-flex
          class="flex"
        >
        
        <v-row>
          
          <v-col>
          <v-card
            class="my-card"
            rounded="xl"
            :loading="isLoading"
            elevation="12"
          >
            <template slot="progress">
              <v-progress-linear
                color="primary"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>
              <v-card-title class="text">Anunciar Manutenção</v-card-title>
              <v-divider/>
              <v-text-field
                  color="primary"
                  v-model="manutencao.motivo"
                  required
                  background-color="transparent"
                  name="motivo"
                  label="Motivo: "
                  type="text"
                ></v-text-field>
                <v-textarea
                  counter
                  v-model="manutencao.desc"
                  name="descricao"
                  label="Descrição"
                  :rules="rules"
                ></v-textarea>
            <v-card-actions>
              <v-row justify="space-between">
                <v-col>
                  <v-btn
                    dark
                    class="btn"
                    @click="register"
                    color="#40A798"
                    block
                    large
                    width="200"
                    :disabled="isLoading"
                  >
                    Enviar
                  </v-btn>
                </v-col>
              </v-row>
            </v-card-actions>
          </v-card>
          </v-col>
          <v-col>
          <div class="flex-column">
            <img
              class="logo"
              :src="require('../assets/logo_transparent.png')"
              alt="icond-Logo"
            />
          </div>
          </v-col>
          </v-row>
        </v-flex>
      </v-layout>
    </v-container>
  </v-main>
    </v-app>
  </div>
</template>
<script>

import axios from "axios"
export default {
  
  name: 'AnunciarManutencao',
  data() {
    return {
      user: { name: "Victor Brasil", function: "Administrador" },
      rules: [v => v.length <= 300 || 'Max 300 characters'],
      manutencao: { motivo: "",
                    desc: "",},
      isLoading: false,
      items: [
          { title: 'Registrar funcionario', icon: 'mdi-plus', link: '/registrar_funcionario'},
          { title: 'Registrar morador', icon: 'mdi-plus', link: '/registrar_morador'},
          { title: 'Administrar Pagamentos', icon: 'mdi-cash', link: '/pagamentos' },
          {title: 'Anunciar manutenção', icon: 'mdi-alert-circle-outline', link: '/anunciar_manutencao'}
        ],
        right: null,
    };
  },
  methods: {
    async register() {
      await axios.post("http://localhost:8080/maintenance/insert/", {
        motive: this.manutencao.motivo,
        description: this.manutencao.desc
      })
      .then(() => {
        alert("Maintenance registered successfully!!")
      })
      .catch((error) => {
        console.log(error)
        alert("An error occurred while trying to register the maintenance")
      })
    }
  }
}
</script>

<style scoped>
body {background-color: #FFEAC9;}
.background {
  background-color: #FFEAC9;
  filter: blur(0,5px);
  height: 100%;
}
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
color: #FFEAC9;
/* elevation/24 */
box-shadow: 0px 11px 15px rgba(0, 0, 0, 0.2);
}
#router-link {
  color:"green";
  text-align: center;
}

.btn {
  border-radius: 12px;
}
h1 {
  color: "red";
  text-align: center;
}
.layout {
  padding: 0;
}

.my-card {
  padding: 2vw 1vw;
  border-radius: 20px;
  z-index: 1;
  position: absolute;
  width: 826px;
  height: 500px;
  left: 150px;
  top: 185px;

}
.divider{
  padding: 20px ;
  }

.flex-column {
  z-index: 0;
  display: flex;
  flex-direction: column;
  top: 300px;
}

.logo {
  width: 150%;
  size: 150%;
  position: relative;
  height: auto;
}

.text {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
font-style: normal;
font-weight: normal;
text-align: center;
font-size: 72px;
line-height: 32px;
letter-spacing: 0.25px;
padding-bottom: 35px;

/* black/0.87 */

color: rgba(0, 0, 0, 0.87);
}

.text-dr {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
text-align: left;
font-size: 23px;
line-height: 10px;
letter-spacing: 0.25px;
color: rgba(0, 0, 0, 0.87);
}
.text-dr-items{
  text-align: left;
  
}
.text-dr-subtitle{
  text-align: left;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  padding-left: 42px;
}
@media (max-width: 1400px) {
  .flex {
    align-items: center;
  }

  .flex-column {
    margin-right: 20px;
  }
}

.flex {
  display: flex;
}

@media (max-width: 1124px) {
  .layout {
    padding: 5vw;
  }
}

@media (max-width: 1024px) {
  .flex {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    justify-items: center;
  }

  .flex-column {
    padding: 10vh;
    align-items: center;
    margin: 0;
  }

  .text {
    text-align: center;
  }
}

@media (max-width: 768px) {
  .flex-column {
    padding: 5vh;
  }
}
</style>