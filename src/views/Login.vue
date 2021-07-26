<template>
    <div>
        <v-app>
            <v-container fluid fill-height class="background">
                <v-layout class="layout" align-center justify-space-between>
                    <v-flex class="flex"
                            xs12
                            sm12
                            md12
                            align-self-center
                            justify-space-between>
                        <v-row>
                            <v-col>
                                <v-card class="my-card"
                                        rounded="xl"
                                        :loading="isLoading">
                                    <template slot="progress">
                                        <v-progress-linear color="primary"
                                                           height="10"
                                                           indeterminate></v-progress-linear>
                                    </template>
                                    <v-card-title class="text"> Login </v-card-title>
                                    <v-spacer class="divider"></v-spacer>
                                    <v-text-field color="primary"
                                                  v-model="user.login"
                                                  background-color="transparent"
                                                  prepend-icon="mdi-account"
                                                  name="login"
                                                  label="Username"
                                                  type="text"></v-text-field>
                                    <v-text-field color="primary"
                                                  v-model="user.password"
                                                  background-color="transparent"
                                                  id="password"
                                                  prepend-icon="mdi-lock"
                                                  name="password"
                                                  label="Password"
                                                  type="password"></v-text-field>
                                    <v-card-actions>
                                        <v-row justify="space-between">
                                            <v-col>
                                                <v-btn dark
                                                       class="btn"
                                                       @click="login"
                                                       color="#40A798"
                                                       block
                                                       large
                                                       width="200"
                                                       :disabled="isLoading">
                                                    Sign In
                                                </v-btn>
                                            </v-col>
                                        </v-row>
                                    </v-card-actions>
                                </v-card>
                            </v-col>
                            <v-col>
                                <div class="flex-column">
                                    <img class="logo"
                                         :src="require('../assets/logo_transparent.png')"
                                         alt="icond-Logo" />
                                </div>
                            </v-col>
                        </v-row>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-app>
    </div>
</template>

<script>

    import axios from "axios";
    export default {
        name: "Login",
        data() {
            return {
                user: { login: "", password: "", },
                isLoading: false,
            };
        },
        methods: {
            async login() {
                var id = null

                const options = {

                    url: "http://localhost:3000/login",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json;charset=UTF-8",
                        "Access-Control-Allow-Origin": "*",
                        "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE",
                        "Access-Control-Allow-Credentials": "true",
                    },
                    data: {
                        username: this.user.login,
                        password: this.user.password,
                    },
                }
                await axios.post(options)
                    .then((response) => {
                        console.log(response)
                        id = response.data.id
                        this.getUser(id)
                    })
                    .catch((error) => {
                        console.log(error)
                        alert("An error occurred while trying to sign up")

                    })
            },
            async getUser(id) {
                console.log(id)
                await axios.get("http://localhost:3000/employee/" + id)
                    .then((response) => {
                        var user = response.data.user
                        if (user === 'Porteiro') {
                            let route = { name: "portaria" };
                            this.$router.push(route);
                        }
                        else if (user === 'Administrador') {
                            let route = { name: "registrar_funcionario" };
                            this.$router.push(route);
                        }
                    })
                    .catch((error) => {
                        console.log(error)
                        alert("An error occurred while trying to sign up")

                    })
            }

        }
    }
</script>
<style scoped>
    body {
        background-color: #FFEAC9;
    }

    .background {
        background-color: #FFEAC9;
        filter: blur(0,5px);
        height: 100%;
    }

    #router-link {
        color: "green";
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
        width: 457px;
        left: 129px;
        top: 227px;
    }

    .divider {
        padding: 10px;
    }

    .flex-column {
        z-index: 0;
        display: flex;
        flex-direction: column;
        top: 300px;
    }

    .logo {
        width: 150%;
        height: auto;
    }

    .text {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-style: normal;
        font-weight: normal;
        font-size: 72px;
        line-height: 32px;
        letter-spacing: 0.25px;
        /* black/0.87 */

        color: rgba(0, 0, 0, 0.87);
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
