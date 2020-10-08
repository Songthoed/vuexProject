<template>
  <div>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field v-model="name" label="Name" required></v-text-field>
      <v-text-field
        v-model="price"
        type="number"
        style="1"
        label="price"
        required
      ></v-text-field>
      <v-file-input
        label="File input"
        v-model="img"
        filled
        prepend-icon="mdi-camera"
      ></v-file-input>
      <v-checkbox
        v-model="status"
        value="WantToBuy"
        label="WantToBuy"
        required
      ></v-checkbox>
      <v-checkbox
        v-model="status"
        value="WantToSell"
        label="WantToSell"
        required
      ></v-checkbox>
      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Validate
      </v-btn>
      <v-btn color="error" class="mr-4" @click="reset"> Reset Form </v-btn>
      <v-btn class="mr-4" @click="page">See all</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    name: "",
    status: "",
    price: "",
    select: null,
    checkbox: false,
    img : null
  }),
  methods: {
    validate() {
      if (this.name) {
        let payload = {
          name: this.name,
          price: this.price,
          status: this.status,
          img: this.img
        };
        this.$store.dispatch("setItem", payload);
      }
    },
    reset() {
      this.$refs.form.reset();
    },
    page() {
      this.$store.state.page = 2;
    },
  },
};
</script>

<style>
</style>