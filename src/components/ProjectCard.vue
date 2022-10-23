<template>
  <v-col xs="12" lg="4" sm="6">
    <v-hover>
      <template v-slot:default="{ hover }">
        <v-card
          class="d-flex flex-column fill-height rounded-lg"
          elevation="8"
          fill-height          
        >
          <v-img :src="item.imagesUrl" height="250" max-height="250"></v-img>
          <v-card-title
            class="text-h6 justify-center text-center"
            v-text="item.title"
          ></v-card-title>
          <v-divider></v-divider>
          <v-card-text
            class="body-2 text-justify align-stretch"
            v-text="item.desc"
          ></v-card-text>
          <v-fade-transition>
            <v-overlay v-if="hover" absolute class="d-flex align-end">
              <v-card-actions class="flex-column">
                <a
                  v-if="item.linkUrl"
                  :href="item.linkUrl"
                  target="_blank"
                  :style="{ width: '100%', textDecoration: 'none'}"
                >
                  <v-btn class="rounded-lg" color="primary" block
                    >Открыть</v-btn
                  >
                </a>
                <a
                  class="mt-2"
                  :href="item.githubUrl"
                  target="_blank"
                  :style="{ width: '100%', textDecoration: 'none' }"
                >
                  <v-btn class="rounded-lg" color="primary" block
                    >Посмотреть на Github</v-btn
                  >
                </a>
              </v-card-actions>
            </v-overlay>
          </v-fade-transition>
        </v-card>
      </template>
    </v-hover>
  </v-col>
</template>

<script>
export default {
  props: ['item'],
};
</script>

<style lang="scss" scoped></style>
