<template>
  <v-layout column>
    <v-flex xs12 sm12 md12>
      <v-card flat>
        <v-img
          height="500"
          class="white--text align-center"
          src="https://images.unsplash.com/photo-1437751695201-298be97a82a8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60"
        >
          <v-card-title class="pa-10 text-left">
            <v-row align="center" justify="center">
              <v-col cols="12" sm="8" md="5">
                <v-card>
                  <v-card-title>
                    <h4 class="text-h6 text-center ma-5">
                      Sign into your account
                    </h4>

                    <p class="text-h7 text-center red--text ma-5" v-if="error">
                      {{ error }}
                    </p>
                  </v-card-title>

                  <v-card-text>
                    <v-form>
                      <v-text-field
                        label="Username"
                        name="login"
                        v-model="login.username"
                        prepend-icon="mdi-account"
                        type="text"
                      ></v-text-field>

                      <v-text-field
                        id="password"
                        label="Password"
                        name="password"
                        v-model="login.password"
                        prepend-icon="mdi-lock"
                        type="password"
                      ></v-text-field>
                    </v-form>
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer />
                    <v-btn
                      color="primary"
                      :disabled="
                        login.username.length == 0 || login.password.length == 0
                      "
                      :loading="loading"
                      class="mb-4 mr-2 pl-5 pr-5"
                      >Sign In</v-btn
                    >
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-card-title>
        </v-img>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data: () => ({
      loading: false,
      login: {
        username: "",
        password: "",
      },
      loading: false,
      error: "",
    }),

    methods: {
      async userLogin() {
        this.loading = true;
        try {
          let response = await this.$auth.loginWith("local", {
            data: this.login,
          });
          this.$auth.setUser(response.data);
          this.$router.push("/");
        } catch (err) {
          if (err.response.status === 401) {
            this.error = "Authentication Failed";
          } else {
            this.error = `Request failed with ${err.response.status}`;
          }
        } finally {
          this.loading = false;
        }
      },
    },
  };
</script>
