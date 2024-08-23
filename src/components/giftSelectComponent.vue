<template>
  <div>
    <h1>{{ name }}!</h1>
    <h1>Izvēlies dāvanu kuru man dāvināsi:</h1>
    <div class="form-check form-switch d-flex">
      <input
        class="form-check-input"
        type="checkbox"
        id="flexSwitchCheckDefault"
        v-model="showRich"
      />
      <label
        class="form-check-label"
        style="margin-left: 10px"
        for="flexSwitchCheckDefault"
      >
        {{ showRich ? "Bagātās aploksnes (drīkst pamēģināt)" : "Nabadzīgās aploksnes" }}
      </label>
    </div>
    <div class="card-container">
      <div
        v-for="card in showRich ? envelopes.rich : envelopes.poor"
        :key="card.amount"
        class="card"
        :class="{ selected: selectedCard === card.amount }"
        :style="{ backgroundImage: `url(${card.image})` }"
        @click="selectCard(card.amount)"
      ></div>
    </div>
    <button
      style="width: 100%"
      type="button"
      class="btn btn-primary mt-3"
      @click="emitAmount"
      :disabled="!selectedCard"
    >
      Dāvināt
    </button>
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
    return {
      selectedCard: null,
      showRich: true,
      envelopes: {
        rich: [
          {
            amount: 500,
            image: "images/500.png",
          },
          {
            amount: 200,
            image: "images/200.jpg",
          },
          {
            amount: 100,
            image: "images/100.jpg",
          },
        ],
        poor: [
          {
            amount: 50,
            image: "images/50.jpg",
          },
          {
            amount: 20,
            image: "images/20.jpg",
          },
          {
            amount: 10,
            image: "images/10.jpg",
          },
        ],
      },
    };
  },
  watch: {
    showRich(newValue) {
      if (!newValue) {
        alert("Tiešām tik traki?");
      }
    },
  },
  methods: {
    selectCard(amount) {
      this.selectedCard = amount;
      // Handle the card selection logic here
      console.log(`Selected card: ${amount} EUR`);
    },
    emitAmount() {
      if (this.selectedCard) {
        this.$emit("amount-selected", this.selectedCard);
      }
    },
  },
};
</script>

<style>
.card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card {
  width: 200px;
  height: 108px;
  background-size: cover;
  display: flex;
  align-items: center;
  margin-top: 10px;
  border: 2px solid transparent;
  cursor: pointer;
  transition: border-color 0.3s;
}

.card:hover {
  border-color: #000;
}

.card.selected {
  border-color: #000;
}

.card-content {
  font-size: 24px;
  color: rgb(244, 0, 0);
  font-weight: bold;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}
</style>