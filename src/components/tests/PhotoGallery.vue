<template>
  <gallery :items="photos">
    <img slot-scope="{item}"
         :src="item.small" />
  </gallery>
</template>

<script>
import Gallery from "../Feed";

export default {
  name: "PhotoGallery",
  components: {
    Gallery
  },
  props: ["photos"]
};
</script>


