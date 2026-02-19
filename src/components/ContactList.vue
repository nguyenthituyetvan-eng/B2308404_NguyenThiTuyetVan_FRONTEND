<script>
export default {
  props: {
    contacts: { type: Array, default: [] },
    activeIndex: { type: Number, default: -1 },
  },
  emits: ["update:activeIndex"],
  methods: {
    updateActiveIndex(index) {
      this.$emit("update:activeIndex", index);
    },
  },
};
</script>

<template>
  <ul class="list-group">
    <li
      class="list-group-item"
      v-for="(contact, index) in contacts"
      :key="contact._id"
      :class="{ active: index === activeIndex }"
      @click="updateActiveIndex(index)"
    >
      {{ contact.name }}
    </li>
  </ul>
</template>
<style scoped>
/* Chữ mặc định màu đen */
.list-group-item {
  cursor: pointer;
  color: black !important;
}

/* Khi được chọn */
.list-group-item.active {
  background-color: #0d6efd; /* màu primary của bootstrap */
  color: white !important;
}
</style>
