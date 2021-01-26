<template>
  <v-app>
    <v-app-bar elevate-on-scroll fixed app>
      <v-toolbar-title
        v-text="title"
        @click="$router.push('/')"
        class="mx-10 title"
      />

      <v-btn text to="/explore">Categories</v-btn>

      <v-text-field
        class="ml-4"
        solo
        dense
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search the world's best photos and images"
      ></v-text-field>
      <v-btn color="warning" class="mr-10">Search</v-btn>

      <v-btn text to="/explore">Explore</v-btn>

      <v-btn outlined color="success" class="mx-5" to="/login">
        <v-icon left>mdi-account-lock</v-icon>
        Login
      </v-btn>

      <v-btn color="success" class="mr-2" to="/register">
        <v-icon left>mdi-account-plus</v-icon>Signup
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer v-bind="localAttrs" padless>
      <v-card flat tile width="100%" class="text-center">
        <v-card-text>
          <v-btn v-for="(i, j) in icons" :key="j" :to="i.to" class="mx-4" icon>
            <v-icon size="24px">
              {{ i.icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text>
          {{ new Date().getFullYear() }} — <strong>{{ title }}</strong>
        </v-card-text>
      </v-card>
    </v-footer>

    <v-dialog v-model="dialog" persistent>
      <v-card>
        <v-img
          :src="image_url"
          contain
          :aspect-ratio="16 / 9"
          lazy-src="https://picsum.photos/id/11/10/6"
        >
          <v-btn color="translucent" icon @click="availDialog(false)">
            <v-icon color="black">mdi-close</v-icon>
          </v-btn>
        </v-img>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
  import { mapState, mapMutations } from "vuex";

  export default {
    computed: {
      ...mapState({
        dialog: (state) => state.dialog,
        image_url: (state) => state.image,
      }),
      localAttrs() {
        const attrs = {};

        if (this.variant === "default") {
          attrs.absolute = false;
          attrs.fixed = false;
        } else {
          attrs[this.variant] = true;
        }
        return attrs;
      },
    },
    data() {
      return {
        clipped: false,
        title: "<CALBASH/>",

        icons: [
          {
            icon: "mdi-home",
            to: "/",
          },
          {
            icon: "mdi-twitter",
            to: "twitter.com/calbashd",
          },
          {
            icon: "mdi-facebook",
            to: "/facebook",
          },
          {
            icon: "mdi-instagram",
            to: "/instagram",
          },
          {
            icon: "mdi-linkedin",
            to: "/linkedin",
          },
          {
            icon: "mdi-folder",
            to: "/careers",
          },
        ],
      };
    },

    methods: {
      ...mapMutations({
        availDialog: "SHOW_DIALOG",
        setImage: "SET_IMAGE",
      }),
    },
  };
</script>