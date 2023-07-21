<script setup>
const props = defineProps({
  path: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: "text-gray-600",
  },
  size: {
    type: String,
    default: "w-4",
  },
});
</script>

<template>
  <div class="relative inline-block badgerr-root">
    <div
      class="absolute top-0 right-0 transform translate-x-1/2 -translate-y-1/2 bg-transparent badgerr-svg"
    >
      <svg
        viewBox="0 0 24 24"
        aria-hidden="true"
        data-view-component="true"
        class="fill-current"
        :class="size + ' ' + color"
      >
        <path :d="path"></path>
      </svg>
    </div>
  </div>
</template>

<style scoped>
.badgerr-root {
}

.badgerr-svg {
}
</style>
