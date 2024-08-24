<template>
  <div>
    <h1>Paldies!!!</h1>
    <h3>Atceramies ka arī 15. septembri vajag brīvu :)</h3>
    <h3>Un neaizmirstam paņemt dvieļus</h3>
    <h3>Tālāk jūs pārvirzīs uz adresi lai varat sagatavoties dāvanai </h3>
    <h2><span>{{ timeout }}</span></h2>
  </div>
</template>

<script>
export default {
  name: "GoodByComponent",
  data() {
    return {
      timeout: 15
    };
  },
  mounted() {
    this.startCountdown();
  },
  methods: {
    startCountdown() {
      const countdownInterval = setInterval(() => {
        if (this.timeout > 0) {
          this.timeout--;
        }
      }, 1000);

      setTimeout(() => {
        clearInterval(countdownInterval);
        window.location.href = "https://smscredit.lv";
      }, 15000);
    }
  }
};
</script>