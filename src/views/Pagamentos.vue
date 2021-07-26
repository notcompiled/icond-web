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
          <v-data-table
          class="my-table"
            :headers="headersFuncionario"
            :items="funcionarios"
            :items-per-page="5"
        ></v-data-table>
        <v-data-table
            class="my-table"
            :headers="headersMoradores"
            :items="moradores"
            :items-per-page="5"
        ></v-data-table>
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
  
  name: 'AnunciarManutencao',
  data() {
    return {
      user: { name: "Victor Brasil", function: "Administrador" },
      headersFuncionario: [
          {
            text: 'Funcionários',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Cargo', value: 'cargo' },
          { text: 'Salário', value: 'salario' },
          { text: 'Data à pagar', value: 'data' },
          { text: 'Status', value: 'status' },
        ],
        funcionarios: [
          {
            name: 'Luan',
            cargo: 'Administrador',
            salario: 2400.30,
            data: 24,
            status: 'falta pagar'
          },
          {
            name: 'Matheus',
            cargo: 'Funcionário Geral',
            salario: 1600.00,
            data: 12,
            status: 'pago',
          },
          {
            name: 'Victor',
            cargo: 'Porteiro',
            salario: 1740.00,
            data: 23,
            status: 'falta pagar',
          },
          {
            name: 'Lucas',
            cargo: 'Porteiro',
            salario: 1740.00,
            data: 7,
            status: 'Pago',
          },
        ],
        headersMoradores: [
          {
            text: 'Moradores',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Apartamento/Casa', value: 'apt' },
          { text: 'Valor do condomínio', value: 'taxa' },
          { text: 'Data à pagar', value: 'data' },
          { text: 'Status', value: 'status' },
        ],
        moradores: [
          {
            name: 'Giovanna',
            apt: '403',
            taxa: 890.30,
            data: 24,
            status: 'falta pagar'
          },
          {
            name: 'Fernando',
            apt: '202',
            taxa: 890.30,
            data: 12,
            status: 'pago',
          },
          {
            name: 'Victor',
            apt: '1002',
            taxa: 890.30,
            data: 23,
            status: 'falta pagar',
          },
          {
            name: 'Luan',
            apt: '703',
            taxa: 890.30,
            data: 7,
            status: 'Pago',
          },
        ],
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

.my-table {
    margin-top: 5vw;
    margin-left: 122px;
    box-shadow: 0px 1px 1px rgba(0, 0, 0, 0.2), 0px 2px 2px rgba(0, 0, 0, 0.14), 0px 1px 5px rgba(0, 0, 0, 0.12);
  border-radius: 20px;
  z-index: 1;
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