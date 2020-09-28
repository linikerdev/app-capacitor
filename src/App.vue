<template>
  <v-app>
    <v-main>
      <div class="openCamera">
        <v-btn class="ma-2" @click="openCamera" tile color="indigo" dark
          >Open Camera</v-btn
        >
      </div>
    </v-main>
  </v-app>
</template>

<script>
import { Plugins, CameraResultType } from "@capacitor/core";
const { Camera } = Plugins;

export default {
  name: "App",

  data: () => ({
    //
  }),
  methods: {
    async openCamera() {
      const image = await Camera.getPhoto({
        quality: 90,
        allowEditing: true,
        resultType: CameraResultType.Uri
      });

      var imageUrl = image.webPath;
      // Can b  e set to the src of an image now
      alert(imageUrl);
      // imageElement.src = imageUrl;
    }
  }
};
</script>

<style lang="scss" scoped>
.openCamera {
  background: #eee;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
