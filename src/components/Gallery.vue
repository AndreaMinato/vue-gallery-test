<template>
  <div class="flex -mx-1">
    <div v-for="type in Object.keys(list)"
         :key="type"
         class="flex-1">
      <img v-for="photo in list[type]"
           :key="photo.id"
           class="p-1 w-full"
           :src="photo.small">
    </div>
  </div>
</template>

<script>
export default {
  name: "Gallery",

  props: {
    photos: {
      required: true
    },
    galleryWidth: {
      required: true
    },
    maxPhotoWidth: {
      default: 200,
      type: Number
    }
  },
  computed: {
    photosSlices() {
      let slices = Math.floor(this.galleryWidth / this.maxPhotoWidth);
      return slices > 0 ? slices : 1;
    },
    list() {
      return this.photos.reduce((columns, photo, index) => {
        var key = index % this.photosSlices;
        columns[key] = columns[key] || [];
        columns[key].push(photo);
        return columns;
      }, {});
    }
  },
  methods: {}
};
</script>


