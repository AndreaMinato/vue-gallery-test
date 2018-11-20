<template>
    <with-dimension>
        <gallery slot-scope="{width}"
                 :gallery-width="width"
                 :items="photos">
            <img slot-scope="{item}"
                 :src="item.small" />
        </gallery>
    </with-dimension>
</template>

<script>
import Gallery from "../Gallery";
import WithDimension from "../WithDimension";

export default {
  name: "PhotoGallery",
  components: {
    Gallery,
    WithDimension
  },
  props: ["photos"]
};
</script>


