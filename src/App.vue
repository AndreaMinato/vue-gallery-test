<template>
  <div id="app"
       class="h-screen flex justify-center">
    <div class="w-5/6 h-full">

      <ul class="py-4 flex justify-around items-center list-reset">
        <li class="cursor-pointer"
            @click="selected = 'photos'">
          Photos
        </li>
        <li class="cursor-pointer"
            @click="selected = 'cards'">
          Card
        </li>
      </ul>

      <div v-show="selected === 'photos'">
        <with-dimension>
          <gallery slot-scope="{width}"
                   :width="width"
                   :items="photos">
            <img slot-scope="{item}"
                 :src="item.small" />
          </gallery>
        </with-dimension>
      </div>

      <div v-show="selected === 'cards'">
        <with-dimension>
          <gallery slot-scope="{width}"
                   :width="width"
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
      </div>
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
  data() {
    return {
      selected: "photos"
    };
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


