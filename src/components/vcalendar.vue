<template>
  <v-date-picker
    :attributes="booked_dates"
    :min-date="new Date()"
    :value="current_date"
    mode="dateTime"
    is24hr
    :disabled-dates="disabled_dates"
    @input="update_date_value($event)"
  >
    <template v-slot="{ inputValue, inputEvents }">
      <b-form-input
        placeholder="Fecha del Taller"
        :value="inputValue"
        v-on="inputEvents"
      />
    </template>
  </v-date-picker>
</template>

<script>
  export default {
    props: ["current_date"],
    methods: {
      update_date_value(event) {
        this.$emit("update:current_date", event);
      },
    },
    mounted() {
      console.log(this.current_date);
    },
    computed: {
      disabled_dates() {
        let res = [];
        for (const event of this.booked_dates) {
          res.push(event.dates);
        }
        return [new Date(), ...res.flat()];
      },
    },
    data() {
      return {
        booked_dates: [
          {
            key: "booked_dates",
            highlight: "red",
            dates: [new Date(2021, 0, 24), new Date(2021, 0, 26)],
          },
        ],
      };
    },
  };

  // //Format
  // Subject
  // Name
  // Discord Username
  // Are you on our server
  // Date
</script>

<style scoped></style>
