<template>
  <v-layout align-center>
    <v-flex fill-height>
      <v-card flat>
        <v-card-title class="my-10 text-left">
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
                  <v-btn text class="mx-2" to="/register">Register</v-btn>
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
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    layout: "auth",
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
