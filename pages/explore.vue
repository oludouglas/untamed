<template>
  <v-layout column>
    <v-flex xs12 sm12 md12>
      <v-row>
        <v-col v-for="(card, i) in tech" :key="i" cols="12" sm="4">
          <v-card class="mx-auto">
            <v-img
              :src="card.imageURL"
              :aspect-ratio="1"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              lazy-src="https://picsum.photos/id/11/10/6"
            >
              <template v-slot:placeholder>
                <v-row class="fill-height ma-0" align="center" justify="center">
                  <v-progress-circular
                    indeterminate
                    color="grey lighten-5"
                  ></v-progress-circular>
                </v-row>
              </template>

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

        {
          id: 4,
          title: "Canon House",
          imageURL:
            "https://images.unsplash.com/photo-1605406233726-81e6e2f52746?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605381078451-a0672a91a4be?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605405809561-2ec85c966680?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605402185149-f796e03bab7a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },

        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605384937950-3939d04810e6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605401443012-7eaeca37b82f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },

        {
          id: 4,
          title: "Canon House",
          imageURL:
            "https://images.unsplash.com/photo-1605401430429-1be9523a39d0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605265058762-a9de6ffc71f6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605407869548-958d58b7cebc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
          detail_link: "/agents",
          loading: false,
        },
        {
          id: 5,
          title: "Camera House",
          imageURL:
            "https://images.unsplash.com/photo-1605420800989-df3eed6214f1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=800&q=60",
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
