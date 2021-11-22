<template>
  <div class="Top">
    <h1>Hello Nuxt</h1>
    <div>
      <button @click="download">download image</button>
    </div>
    <div>
      <nuxt-link to="/category">jump to Category</nuxt-link>
    </div>
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
} from '@nuxtjs/composition-api';
import { exportImgData } from "@/components/Top/exportImgData";
import base64ToBlob from 'b64-to-blob';
import { saveAs } from 'file-saver';

export default defineComponent({
  components: {
  },
  props: {
  },
  setup(props, { emit }) {
    const base64 = exportImgData();
    const download = () => {
      const fileURL = URL.createObjectURL(base64ToBlob(base64.replace(/^.*,/, ''), 'image/jpeg'));
      const fileName = 'sample.jpeg';

        saveAs(fileURL, fileName);
    }
    return {
      download,
    }
  },
});
</script>

<style scoped>

</style>
