<template>
  <Layout>
    <!-- <validation-observer ref="observer"> -->
    <form class="center mb-4 mt-3">
      <h3>Contact us</h3>
      <!-- <validation-provider -->
      <!-- v-slot="{ errors }" name="Name" rules="required|max:10" > -->
      <v-text-field
        v-model="name"
        :counter="10"
        :error-messages="errors"
        label="Name"
        required
      ></v-text-field>
      <!-- </validation-provider> -->
      <!-- <validation-provider -->
      <!-- v-slot="{ errors }" name="email" rules="required|email" > -->
      <v-text-field
        v-model="email"
        :error-messages="errors"
        label="E-mail"
        required
      ></v-text-field>
      <!-- </validation-provider> -->
      <!-- <validation-provider v-slot="{ errors }" name="select" rules="required"> -->
      <v-select
        v-model="select"
        :items="items"
        :error-messages="errors"
        label="Query type"
        data-vv-name="select"
        required
      ></v-select>
      <!-- </validation-provider> -->
      <v-textarea
        outlined
        name="input-7-4"
        label="What problem do you have"
        value="Tell us more about the problem"
      ></v-textarea>
      <v-textarea
        outlined
        name="input-7-4"
        label="What's your business like"
        value="Tell us more about your business"
      ></v-textarea>
      <v-btn class="mr-4" @click="submit"> Send </v-btn>
      <v-btn @click="clear"> Clear </v-btn>
    </form>
    <!-- </validation-observer> -->
    <div class="separator"></div>
  </Layout>
</template>

<script>
// import { required, email, max } from "vee-validate/dist/rules";
// import {
//   extend,
//   ValidationObserver,
//   ValidationProvider,
//   setInteractionMode,
// } from "vee-validate";

// setInteractionMode("eager");

// extend("required", {
//   ...required,
//   message: "{_field_} can not be empty",
// });

// extend("max", {
//   ...max,
//   message: "{_field_} may not be greater than {length} characters",
// });

// extend("email", {
//   ...email,
//   message: "Email must be valid",
// });

export default {
  components: {
    // ValidationProvider,
    // ValidationObserver,
  },
  data: () => ({
    name: "",
    email: "",
    select: null,
    errors: null,
    items: ["Orders", "Delivery", "Tech support", "Refund"],
    checkbox: null,
  }),

  methods: {
    submit() {
      // this.$refs.observer.validate();
    },
    clear() {
      this.name = "";
      this.email = "";
      this.select = null;
      this.checkbox = null;
      // this.$refs.observer.reset();
    },
  },
};
</script>
<style>
.center {
  margin: auto;
  width: 60%;
  padding: 10px;
}
</style>
