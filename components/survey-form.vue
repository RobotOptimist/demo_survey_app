<template>
  <b-container fluid>
    <b-form-row>
      <b-col sm="3">
        <label for="serial-serialNumber">Hydrant Serial serialNumber</label>
      </b-col>
      <b-col sm="9">
        <b-form-input
          type="text"
          v-model="serialNumber"
          id="serial-serialNumber"
          placeholder="Enter the hydrant serial serialNumber"
        ></b-form-input>
      </b-col>
    </b-form-row>
    <b-form-row>
      <b-col sm="3">
        <label for="condition">Hydrant Condition</label>
      </b-col>
      <b-col sm="9">
        <b-form-select v-model="condition" :options="options" id="condition"></b-form-select>
      </b-col>
    </b-form-row>
    <b-row align-h="end" class="p-3">
        <b-col cols="*">
            <b-button @click="submit">Submit</b-button>
        </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      serialNumber: "",
      condition: null,
      options: [
        { value: null, text: "Please choose a hydrant condition." },
        { value: "poor", text: "Poor" },
        { value: "fair", text: "Fair" },
        { value: "good", text: "Good" },
        { value: "excellent", text: "Excellent" },
      ],
    };
  },
  methods: {
    submit() {
      console.log('submitted')
      const serialNumber = this.serialNumber;
      const condition = this.condition;
      this.$emit("submitForm", { serialNumber, condition });
      this.serialNumber = '';
      this.condition = null;
    },
  },
};
</script>