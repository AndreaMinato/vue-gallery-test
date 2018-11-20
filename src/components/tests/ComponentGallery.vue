<template>
  <gallery :items="photos">
    <div slot-scope="{item}"
         class="flex flex-col p-2 border">
      <h4><a :href="item.regular"
           target="_blank">
          {{item.id}}
        </a> </h4>
      <img class="my-2"
           :src="item.thumb" />
      <p>{{item.description}}</p>
    </div>
  </gallery>
</template>

<script>
import Gallery from "../Feed";

export default {
  name: "ComponentGallery",
  components: {
    Gallery
  },
  props: ["photos"]
};
</script>


