<template>
  <v-app>
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
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        dialog: false,
        clipped: false,
        title: "<CALBASH/>",

        icons: [
          {
            icon: "mdi-home",
            to: "/",
          },
          {
            icon: "mdi-twitter",
            to: "/twotter",
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
    computed: {
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
  };
</script>