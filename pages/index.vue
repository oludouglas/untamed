<template>
  <v-layout column>
    <v-flex xs12 sm12 md12>
      <v-card flat>
        <v-img
          height="450"
          aspect-ratio="1"
          class="white--text align-center"
          src="https://images.unsplash.com/photo-1437751695201-298be97a82a8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60"
        >
          <v-card-title class="pa-10 text-left">
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <div class="text-h4 mb-5">
                  <b>Splash</b>
                </div>
                <div class="text-h6">
                  The internet’s source of freely-usable images. Powered by
                  creators everywhere.
                </div>
              </v-col>
              <v-col cols="12" sm="12" md="12">
                <v-btn large class="pa-6" color="primary" to="/how_it_works">
                  Take the first step
                  <v-icon>mdi-arrow-right</v-icon>
                </v-btn>
              </v-col>

              <v-col cols="12" sm="12" md="12" class="">
                Photo of the day
              </v-col>
            </v-row>
          </v-card-title>
        </v-img>
      </v-card>

      <v-row class="mt-16 ml-5 mr-5 mb-16">
        <v-col v-for="(card, i) in tech" :key="i" cols="12" sm="4">
          <v-card class="mx-auto">
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
  export default {
    data: () => ({
      loading: false,

      tech: [
        {
          id: 2,
          title: "Caravella",
          imageURL:
            "https://images.unsplash.com/photo-1605370458667-56d9dddabbea?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 3,
          title: "Sony House",
          imageURL:
            "https://images.unsplash.com/photo-1605443791607-80a259dd3c3c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 4,
          title: "Canon House",
          imageURL:
            "https://images.unsplash.com/photo-1605398920523-26470ee935f6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1523217582562-09d0def993a6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1416331108676-a22ccb276e35?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1452626212852-811d58933cae?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },

        {
          id: 3,
          title: "Sony House",
          imageURL:
            "https://images.unsplash.com/photo-1605365070248-299a182a2ca6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 4,
          title: "Canon House",
          imageURL:
            "https://images.unsplash.com/photo-1449844908441-8829872d2607?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605020800962-8c58acb6e10b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1416331108676-a22ccb276e35?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1452626212852-811d58933cae?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
      ],
      loading: false,
    }),

    methods: {
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
