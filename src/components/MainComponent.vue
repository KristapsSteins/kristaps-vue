<template>
  <div>
    <IntroductionComponent v-if="!nameSubmitted" @name-changed="handleNameChange" />
    <GiftSelectComponent v-if="nameSubmitted" :name="receivedName" />
  </div>
</template>

<script>
import IntroductionComponent from "./introductionComponent.vue";
import GiftSelectComponent from "./giftSelectComponent.vue";

export default {
  name: "MainComponent",
  components: {
    IntroductionComponent,
    GiftSelectComponent,
  },
  data() {
    return {
      receivedName: "",
      nameSubmitted: false,
    };
  },
  methods: {
    handleNameChange(name) {
      this.receivedName = name;
      this.nameSubmitted = true;
    },
  },
};
</script>