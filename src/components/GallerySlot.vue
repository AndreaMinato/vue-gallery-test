<template>
  <div class="flex -mx-1">
    <div v-for="type in Object.keys(list)"
         :key="type"
         class="flex-1">
      <div v-for="(item, index) in list[type]"
           :key="index"
           class="p-1 w-full">
        <slot :item="item"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Gallery",

  props: {
    items: {
      required: true
    },
    width: {
      required: true
    },
    maxColumnWidth: {
      default: 200,
      type: Number
    }
  },
  computed: {
    columns() {
      let slices = Math.floor(this.width / this.maxColumnWidth);
      return slices > 0 ? slices : 1;
    },
    list() {
      return this.items.reduce((columns, item, index) => {
        var key = index % this.columns;
        columns[key] = columns[key] || [];
        columns[key].push(item);
        return columns;
      }, {});
    }
  },
  methods: {}
};
</script>


