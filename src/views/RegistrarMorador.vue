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
              <v-card-title class="text">Registrar Morador</v-card-title>
              <v-spacer class="divider"></v-spacer>
              <v-divider/>
              <v-row>
              <v-col>
                <v-text-field
                  color="primary"
                  v-model="newUser.name"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-account-outline"
                  name="name"
                  label="Full name"
                  type="text"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.email"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-email-outline"
                  name="email"
                  label="Email"
                  type="text"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.phone"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-phone-outline"
                  name="phone"
                  label="Phone"
                  type="text"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.dataPagamento"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-calendar-range"
                  name="dataPagamento"
                  label="Data de Pagamento"
                  type="text"
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  color="primary"
                  v-model="newUser.login"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-account"
                  name="username"
                  label="Username"
                  type="text"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.password"
                  required
                  background-color="transparent"
                  id="password"
                  prepend-icon="mdi-lock"
                  name="password"
                  label="Password"
                  type="password"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.cpf"
                  required
                  background-color="transparent"
                  prepend-icon="mdi-card-account-details-outline"
                  name="cpf"
                  label="CPF"
                  type="text"
                ></v-text-field>
                <v-text-field
                  color="primary"
                  v-model="newUser.function"
                  requierd
                  background-color="transparent"
                  prepend-icon="mdi-home-outline"
                  name="apt"
                  label="Casa/apt"
                  type="text"
                ></v-text-field>
                </v-col>
              </v-row>
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
                    Registrar
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
export default {
  
  name: 'RegistrarMorador',
  data() {
    return {
      user: { name: "Victor Brasil", function: "Administrador" },
      newUser: {
                    name: "",
                    email: "",
                    phone: "",
                    dataPagamento: "",
                    username: "",
                    cpf: "",
                    apt:""},
      isLoading: false,
      items: [
          { title: 'Registrar funcionario', icon: 'mdi-plus', link: '/registrar_funcionario'},
          { title: 'Registrar morador', icon: 'mdi-plus', link: '/registrar_morador'},
          { title: 'Administrar Pagamentos', icon: 'mdi-cash', link: '/pagamentos' },
          {title: 'Anunciar manutenção', icon: 'mdi-alert-circle-outline', link: '/anunciar_manutencao'}
        ],
        right: null,
    };
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