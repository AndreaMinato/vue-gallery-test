<script>
import ResizeObserver from "resize-observer-polyfill";

export default {
  data() {
    return {
      width: null,
      height: null
    };
  },
  mounted() {
    var observer = new ResizeObserver(entries => {
      for (let entry of entries) {
        const cr = entry.contentRect;
        this.width = cr.width;
        this.heigth = cr.height;
      }
    });

    // Observe one or multiple elements
    observer.observe(this.$el);
  },
  render() {
    return this.$scopedSlots.default({
      width: this.width,
      height: this.height
    });
  }
};
</script>
