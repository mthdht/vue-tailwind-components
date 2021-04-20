<script>

export default {
  name: 'vt-button', // vue component name
  props: {
    "size": {
      type: String,
      default: null,
      validator: function (value) {
        return ["sm", "md", "lg", "xl"].indexOf(value) !== -1
      }
    },
    "type": {
      type: String,
      default: null,
      validator: function (value) {
        return ["success", "warning", "danger", "none"].indexOf(value) !== -1
      }
    },
    "rounded": {
      type: String,
      default: null,
      validator: function (value) {
        return ["sm", "md", "lg", "xl", "2xl", "full", "none"].indexOf(value) !== -1
      },
    },
    "outline": {
      type: Boolean,
      default: false
    }
  },
  computed: {
    classes() {
      let classes = "focus:outline-none "
      switch (this.type) {
        case "success":
          classes += this.outline ? "text-green-600 border-2 border-green-500" : "bg-green-500 text-white"
          classes += " font-bold hover:bg-green-600 hover:text-white focus:ring focus:ring-green-500 focus:ring-opacity-50"
          break;
        case "danger":
          classes += this.outline ? "text-red-600 border-2 border-red-500" : "bg-red-500 text-white"
          classes += " font-bold hover:bg-red-600 hover:text-white focus:ring focus:ring-red-500 focus:ring-opacity-50"
          break;
        case "warning":
          classes += this.outline ? "text-yellow-600 border-2 border-yellow-500" : "bg-yellow-500 text-white"
          classes += " font-bold hover:bg-yellow-600 hover:text-white focus:ring focus:ring-yellow-500 focus:ring-opacity-50"
          break;
        case "none":
          classes += ""
          break;
        default:
          classes += this.outline ? "text-gray-600 border-2 border-gray-500" : "bg-gray-200 text-gray-700"
          classes += " font-bold hover:bg-gray-500 hover:text-white focus:ring focus:ring-gray-500 focus:ring-opacity-50"
          break;
      }

      switch (this.size) {
        case "sm":
        case "md":
        case "lg":
          classes += " px-4 py-2 text-" + this.size
          break;
        case "xl":
        case "2xl":
          classes += " px-5 py-3 text-" + this.size
          break;
        default:
          classes += " px-4 py-2"
          break;
      }

      switch (this.rounded) {
        case "sm":
        case "md":
        case "lg":
        case "xl":
        case "2xl":
        case "full":
        case "none":
          classes += " rounded-" + this.rounded
          break;
        default:
          classes += " rounded"
          break;
      }

      return classes
    }
  }
};
</script>

<template>
  <button :class="this.classes">
      <slot></slot>
  </button>
</template>

<style scoped>

</style>