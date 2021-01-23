<template>
  <form @submit.prevent>
    <h3>¿Quieres hacer un taller con nosotros?</h3>
    <h5>¡Rellena este formulario y te contactaremos mediante Discord!</h5>
    <b-input-group>
      <b-input
        class="mb-3"
        placeholder="Nombre y Apellido"
        type="text"
      ></b-input>
      <b-input
        class="mb-3"
        placeholder="Tópico del Taller"
        type="text"
      ></b-input>
      <vcalendar
        class="mb-3"
        id="date-picker"
        :current_date.sync="current_date"
      />
      <b-input
        class="mb-3"
        placeholder="Usuario de Discord"
        type="text"
      ></b-input>
    </b-input-group>
  </form>
</template>

<script>
  import vcalendar from "./vcalendar";
  export default {
    components: {
      vcalendar,
    },
    data() {
      return {
        current_date: undefined,
      };
    },
    methods: {
      send_data() {
        console.log();
      },
    },
  };
</script>

<style scoped>
  form,
  .input-group {
    display: flex;
    flex-flow: column nowrap;
    justify-content: space-around;
    align-items: center;
  }
  form {
    height: 40vh;
  }
  input,
  #date-picker {
    min-width: 40vw !important;
  }
</style>
