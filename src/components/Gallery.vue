<template>
  <div class="container-flex">
    <div v-for="type in Object.keys(list)"
         :key="type"
         class="flex-1">
      <div v-for="(item, index) in list[type]"
           :key="index">
        <slot :item="item"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueColumnsGallery",

  props: {
    items: {
      required: true
    },
    galleryWidth: {
      required: true,
      type: Number
    },
    columnWidth: {
      type: Number,
      default: 0
    },
    maxColumns: {
      type: Number,
      default: 0
    }
  },
  computed: {
    columns() {
      let columns = Math.floor(this.galleryWidth / this.columnWidth);
      return columns > 0 ? columns : 1;
    },
    list() {
      return this.items.reduce((columns, item, index) => {
        var key = index % this.columns;
        columns[key] = columns[key] || [];
        columns[key].push(item);
        return columns;
      }, {});
    }
  }
};
</script>

<style>
  .container-flex {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .flex-1 {
    flex: 1;
  }
</style>



