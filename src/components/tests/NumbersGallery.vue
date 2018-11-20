<template>
  <feed class="-mx-2"
        :max-columns="3"
        :column-width="250"
        :items="numbers">
    <div slot-scope="{item}"
         class="bg-green-dark border border-grey p-4 m-2"
         v-text="item" />
  </feed>
</template>

<script>
import Feed from "../Feed";

export default {
  name: "NumbersGallery",
  components: {
    Feed
  },
  props: ["numbers"]
};
</script>


