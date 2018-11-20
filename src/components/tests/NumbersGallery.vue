<template>
  <with-dimension>
    <gallery slot-scope="{width}"
             :gallery-width="width"
             class="-mx-2"
             :items="numbers">
      <div slot-scope="{item}"
           class="bg-green-dark border border-grey p-4 m-2"
           v-text="item" />
    </gallery>
  </with-dimension>
</template>

<script>
import Gallery from "../Gallery";
import WithDimension from "../WithDimension";

export default {
  name: "NumbersGallery",
  components: {
    Gallery,
    WithDimension
  },
  props: ["numbers"]
};
</script>


