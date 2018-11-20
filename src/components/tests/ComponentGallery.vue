<template>
  <with-dimension>
    <gallery slot-scope="{width}"
             :gallery-width="width"
             :items="photos">
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
  </with-dimension>
</template>

<script>
import Gallery from "../Gallery";
import WithDimension from "../WithDimension";

export default {
  name: "ComponentGallery",
  components: {
    Gallery,
    WithDimension
  },
  props: ["photos"]
};
</script>


