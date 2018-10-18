<template>
  <div id="app"
       class="h-screen flex justify-center">
    <div class="container h-full">
      <with-dimension>
        <gallery slot-scope="{width}"
                 :gallery-width="width"
                 :photos="photos" />
      </with-dimension>
    </div>
  </div>
</template>

<script>
import Gallery from "./components/Gallery";
import WithDimension from "./components/WithDimension";

import photos from "./photos.js";

export default {
  name: "app",
  components: {
    Gallery,
    WithDimension
  },
  computed: {
    photos() {
      return photos.map(photo => {
        return {
          id: photo.id,
          created_at: photo.created_at,
          thumb: photo.urls.thumb,
          small: photo.urls.small,
          regular: photo.urls.regular,
          description: photo.description,
          download: `${
            photo.links.download_location
          }/?client_id=f96ed367d8127eb886407fb3b4707af08ad1f7057c93c0a8a0ac00f4b064d86c`
        };
      });
    }
  }
};
</script>


