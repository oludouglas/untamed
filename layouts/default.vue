<template>
  <v-app>
    <v-app-bar :clipped-left="clipped" fixed app flat>
      <v-list-item-avatar tile color="grey">
        <v-img
          class="white--text align-start"
          aspect-ratio="1"
          src="logo.png"
        ></v-img>
      </v-list-item-avatar>
      <v-toolbar-title
        v-text="title"
        @click="$router.push('/')"
        class="mr-15"
      />

      <v-text-field
        class="ml-16"
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search the world's best photos and images"
      ></v-text-field>

      <v-btn text class="ma-2" to="/explore">Explore</v-btn>

      <v-btn text color="info" @click="dialog = !dialog" class="ma-2">
        <v-icon left>mdi-upload</v-icon>Submit photo
      </v-btn>
      <v-divider vertical />
      <v-btn text class="ma-2" to="/login"> Login </v-btn>

      <v-btn color="success" class="mr-2" to="/register">
        <v-icon left>mdi-account-plus</v-icon>Join free
      </v-btn>
    </v-app-bar>

    <v-main>
      <nuxt />
    </v-main>

    <v-footer color="purple lighten-1" class="mt-0" padless>
      <v-row justify="center" no-gutters>
        <v-col cols="12" class="text-center ma-5">
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px"> mdi-facebook </v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px"> mdi-twitter </v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px"> mdi-whatsapp </v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px"> mdi-instagram </v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px"> mdi-linkedin </v-icon>
          </v-btn>
        </v-col>

        <v-col class="text-center white--text" cols="3"> Untamd Inc </v-col>
        <v-col class="text-center white--text" cols="3"> Tenants </v-col>
        <v-col class="text-center white--text" cols="3"> Landlords </v-col>
        <v-col class="text-center white--text" cols="3"> Others </v-col>

        <v-col class="text-center white--text" cols="3"> Careers </v-col>
        <v-col class="text-center white--text" cols="3">
          Terms and conditions
        </v-col>
        <v-col class="text-center white--text" cols="3"> How to rent </v-col>
        <v-col class="text-center white--text" cols="3"> Others </v-col>

        <v-col class="text-center white--text" cols="3"> Data Security </v-col>
        <v-col class="text-center white--text" cols="3"> Pricing </v-col>
        <v-col class="text-center white--text" cols="3"> </v-col>
        <v-col class="text-center white--text" cols="3"> </v-col>

        <v-col class="text-center white--text" cols="3"> Cookie policy </v-col>
        <v-col class="text-center white--text" cols="3"> Blog for inter </v-col>
        <v-col class="text-center white--text" cols="3"> </v-col>
        <v-col class="text-center white--text" cols="3"> </v-col>

        <v-col class="text-center white--text mb-10" cols="12">
          {{ new Date().getFullYear() }} — <strong>Untamd</strong>
        </v-col>
      </v-row>
    </v-footer>

    <v-dialog v-model="dialog" max-width="700">
      <v-card>
        <v-card-title class="headline">
          Upload up to 6 photos or images at a time
        </v-card-title>

        <v-card-text>
          <v-row justify="space-around">
            <v-col v-for="i in 6" :key="i" cols="12" md="4">
              <v-sheet class="pa-12" color="grey lighten-3">
                Click to attach
              </v-sheet>
            </v-col>
          </v-row>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn color="warning darken-1" text @click="dialog = false">
            Cancel
          </v-btn>

          <v-btn color="green darken-1" text @click="dialog = false">
            Upload
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        dialog: false,
        clipped: false,
        title: "Untamd",
      };
    },
  };
</script>