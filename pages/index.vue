<template>
  <v-layout column>
    <v-flex xs12 sm12 md12>
      <v-row class="mx-2">
        <v-col v-for="(card, i) in tech" :key="i" cols="12" sm="4">
          <v-card class="mx-auto" @click="showDialog(card.imageURL)">
            <v-img
              :src="card.imageURL"
              :aspect-ratio="1"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              lazy-src="https://picsum.photos/id/11/10/6"
            >
              <v-card-title class="white--text">
                <v-row>
                  <v-col md="10"> {{ card.title }} </v-col>
                  <v-col md="2" class="text-right">
                    <v-icon
                      color="white"
                      v-show="!loading"
                      @click="downloadImage(card.imageURL)"
                      >mdi-download</v-icon
                    >
                  </v-col>
                </v-row>
              </v-card-title>
            </v-img>
          </v-card>
        </v-col>
      </v-row>
    </v-flex>
  </v-layout>
</template>

<script>
  import { mapState, mapMutations } from "vuex";
  export default {
    computed: {
      ...mapState({
        dialog: (state) => state.dialog,
        imageURL: (state) => state.image,
        tech: (state) => state.photos,
        loading: (state) => state.loading,
      }),
    },
    data: () => ({}),

    methods: {
      ...mapMutations({
        availDialog: "SHOW_DIALOG",
        setImage: "SET_IMAGE",
      }),
      showDialog(imgURL) {
        if (!imgURL) return;
        this.setImage(imgURL);
        this.availDialog(true);
      },
      downloadImage(url) {
        this.loading = true;
        this.$axios
          .get(url, {
            responseType: "blob",
          })
          .then((res) => {
            const blob = new Blob([res.data], { type: "application/image" });
            const link = document.createElement("a");
            link.href = URL.createObjectURL(blob);

            link.click();
            URL.revokeObjectURL(link.href);
          })
          .catch((er) => {
            console.log(er);
          })
          .finally(() => {
            this.loading = false;
          });
      },
    },
  };
</script>
