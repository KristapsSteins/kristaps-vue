<template>
    <div>
      <div class="d-flex flex-column gap-3">
        <h1>Kristapam 30!!!</h1>
        <h3>Ielūdzu tevi uz savām dzimšanas dienas svinībām</h3>
        <h4>Laiks: 15:00</h4>
        <h4>Datums: 2024. gada 14. septembrs</h4>
        <h4>Vieta: Vīgriežu iela 39-2, Jelgava, Latvija</h4>
        <h3>Lūdzu apstirpini savu ierašanos</h3>
      </div>
      <div class="form-group mt-3">
        <input
          type="text"
          class="form-control"
          id="name"
          placeholder="Čomiņ, ievadi savu vārdu"
          v-model="name"
        />
        <button
          style="width: 100%"
          type="button"
          class="btn btn-primary mt-3"
          @click="emitName"
          :disabled="!isNameValid"
        >
          Saglabāt
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "IntroductionComponent",
    data() {
      return {
        name: "",
      };
    },
    computed: {
      isNameValid() {
        return this.name.length >= 3;
      },
    },
    methods: {
      emitName() {
        if (this.isNameValid) {
          this.$emit("name-changed", this.name);
        }
      },
    },
  };
  </script>