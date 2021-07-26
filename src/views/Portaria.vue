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

        <v-flex class="flex"
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
              <v-row>
                  <v-col>
                  <div class="flex-column">
                        <img
                        class="selfie"
                        src='../assets/pabllo-selfie.jpg'
                        alt="morador"
                        />
                    </div>
                  </v-col>
                <v-col>
                    <v-btn
                    class="btn2"
                    dark
                    @click="read"
                    color="#40A798"
                    block
                    large
                    :disabled="isLoading"
                  >
                    Ler passe de entrada
            </v-btn>
                    <v-card-text class="text">
                    <div class="text-title"> 
                        {{userEntrada.name}}
                    </div>
                    <div class="text-subtitle">
                        {{userEntrada.function}}
                    </div>
                    <div class="text-subtitle">
                        {{userEntrada.apt}}
                    </div>
                    </v-card-text>
                </v-col>
              </v-row>
            <v-card-actions>
              <v-row >
                  <v-spacer/>
                <v-col>
                  <v-btn
                  dark
                    class="btn"
                    @click="register"
                    color="#40A798"
                    large
                    block
                    :disabled="isLoading"
                  >
                    Registrar Entrada
                  </v-btn>
                </v-col>
              </v-row>
            </v-card-actions>
          </v-card>
            <v-card
            class="my-card2"
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
              <v-row>
                  <v-col>
                  <div class="flex-column">
                        <img
                        class="selfie"
                        src='../assets/beyonce-selfie.jpg'
                        alt="morador"
                        />
                    </div>
                  </v-col>
                <v-col>
                <v-btn class="btn2"
                    dark
                    @click="read"
                    color="#40A798"
                    block
                    large
                    :disabled="isLoading"
                  >
                    Ler passe Saída
                </v-btn>
                    <v-card-text class="text">
                    <div class="text-title"> 
                        {{userSaida.name}}
                    </div>
                    <div class="text-subtitle">
                        {{userSaida.function}}
                    </div>
                    <div class="text-subtitle">
                        {{userSaida.apt}}
                    </div>
                    </v-card-text>
                </v-col>
              </v-row>
            <v-card-actions>
              <v-row >
                  <v-spacer/>
                <v-col>
                  <v-btn
                  dark
                    class="btn"
                    @click="register"
                    color="#40A798"
                    large
                    block
                    :disabled="isLoading"
                  >
                    Registrar Saída
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
  
  name: 'Portaria',
  data() {
    return {
      user: { name: "Victor Brasil", function: "Porteiro" },
      userEntrada: {name: "Pabllo Vittar", function: "Morador", apt:"403", image: '../assets/pabllo-selfie.jpg'},
      userSaida: {name: "Beyoncé Knowles", function: "Visitante", apt:"1002", image:'../assets/beyonce-selfie.jpg'},
      isLoading: false,
      items: [
          { title: 'Entrada e saída', icon: 'mdi-plus', link: '/portaria'},
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
width: 400px;
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
  margin-right: 10px;
}
.btn2{
right: 30px;
background: #40A798;
border-radius: 44px;
}
.layout {
  padding: 0;
}

.my-card {
width: 754px;
height: 345px;
left: 122px;
z-index: 3;
margin-top: 60px;
background: #FFFFFF;
box-shadow: 0px 4px 4px 5px rgba(0, 0, 0, 0.25);
border-radius: 20px;
}
.my-card2 {
    z-index: 3;
width: 754px;
height: 345px;
left: 122px;
margin-top: 30px;
background: #FFFFFF;
box-shadow: 0px 4px 4px 5px rgba(0, 0, 0, 0.25);
border-radius: 20px;
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
.selfie{
    width: 200px;
    border-radius: 20px;
    margin-left: 58px;
    margin-top: 48px;
    aspect-ratio: 1/1;
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
text-align: right;
}
.text-title{
font-weight: 500;
font-size: 36px;
line-height: 32px;
letter-spacing: 0.25px;
color: rgba(0, 0, 0, 0.87);
}
.text-subtitle{
font-size: 24px;
line-height: 22px;

letter-spacing: 0.1px;
color: rgba(0, 0, 0, 0.6);
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