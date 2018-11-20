<template>
  <div class="container-flex">
    <div v-for="column in Object.keys(list)"
         :key="column"
         class="flex-1">
      <div v-for="(item, index) in list[column]"
           :key="index">
        <slot :item="item"></slot>
      </div>
    </div>
  </div>
</template>

<script>
import ResizeObserver from "resize-observer-polyfill";

export default {
  name: "VueFeed",

  props: {
    items: {
      required: true
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
  mounted() {
    var observer = new ResizeObserver(entries => {
      for (let entry of entries) {
        const cr = entry.contentRect;
        this.width = cr.width;
        //   this.heigth = cr.height;
      }
    });

    // Observe one or multiple elements
    observer.observe(this.$el);
  },
  data() {
    return {
      width: 0
    };
  },
  computed: {
    columns() {
      let columns;
      columns =
        this.columnWidth > 0
          ? Math.floor(this.width / this.columnWidth)
          : this.maxColumns;

      columns = columns < this.maxColumns ? columns : this.maxColumns;

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



