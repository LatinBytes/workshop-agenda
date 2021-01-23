<template>
  <div class="home">
    <workshopForm />
  </div>
</template>

<script>
  import workshopForm from "../components/workshop_form.vue";

  export default {
    data() {
      return {};
    },
    name: "Home",
    components: {
      workshopForm,
    },
  };
</script>
