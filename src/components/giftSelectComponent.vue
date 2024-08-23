<template>
  <div>
    <h1>{{ name }}!</h1>
    <h1>Izvēlies dāvanu:</h1>
  </div>
</template>

<script>
export default {
  name: "GiftSelectComponent",
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  data() {
  },
  methods: {
  },
};
</script>
