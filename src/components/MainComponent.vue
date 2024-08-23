<template>
  <div class="bg">
    <IntroductionComponent v-if="!nameSubmitted" @name-changed="handleNameChange" />
    <GiftSelectComponent v-if="nameSubmitted && !amountSubmitted" :name="receivedName" @amount-selected="handleAmountChange"/>
    <GoodByComponent v-if="amountSubmitted"/>
  </div>
</template>

<script>
import IntroductionComponent from "./introductionComponent.vue";
import GiftSelectComponent from "./giftSelectComponent.vue";
import GoodByComponent from "./goodByComponent.vue";

export default {
  name: "MainComponent",
  components: {
    IntroductionComponent,
    GiftSelectComponent,
    GoodByComponent
  },
  data() {
    return {
      receivedName: "",
      nameSubmitted: false,
      amount: 0,
      amountSubmitted: false,
    };
  },
  methods: {
    handleNameChange(name) {
      this.receivedName = name;
      this.nameSubmitted = true;
    },
    handleAmountChange(amount) {
      console.log(amount);
      this.amount = amount;
      this.amountSubmitted = true;
    },
  },
};
</script>