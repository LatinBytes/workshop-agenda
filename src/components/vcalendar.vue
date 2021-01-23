<template>
  <v-date-picker
    :attributes="booked_dates"
    :min-date="new Date()"
    :value="current_date || undefined"
    mode="dateTime"
    is24hr
    :disabled-dates="disabled_dates"
    @input="update_date_value($event)"
    ref="calendar"
  >
    <template v-slot="{ inputValue, inputEvents }">
      <b-form-input
        placeholder="Fecha del Taller"
        :value="inputValue"
        v-on="inputEvents"
        readonly
      />
    </template>
    <template #footer>
      <span class="footer_of_calendar">
        <b-button @click="save_value()" size="sm" variant="outline-info">
          Guardar
        </b-button>
        <b-button
          @click="handle_cancelation()"
          size="sm"
          variant="outline-danger"
        >
          Cancel
        </b-button>
      </span>
    </template>
  </v-date-picker>
</template>

<script>
  export default {
    props: ["current_date"],
    methods: {
      save_value() {
        this.$refs.calendar.updateValue(this.current_date, {
          formatDate: true,
          hidePopover: true,
        });
      },
      handle_cancelation() {
        this.$refs.calendar.updateValue("", { hidePopover: true });
      },
      update_date_value(event) {
        this.$emit("update:current_date", event);
      },
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

<style scoped>
  input {
    background-color: rgb(255, 255, 255) !important;
  }
  .footer_of_calendar {
    display: flex;
    justify-content: space-around;
    margin: 1vh 0;
  }
</style>
