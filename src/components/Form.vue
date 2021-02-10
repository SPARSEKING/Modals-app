<template>
  <form>
    <label>Name:</label>
    <input type="text" v-modal="modalSecond.name" />
    <label>Email:</label>
    <input type="text" v-modal="modalSecond.email" />
    <button class="btn btnPrimary">
      Submit!
    </button>
  </form>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { ModalSecond } from "../ModalSecond";

export default defineComponent({
  name: "Form",
  data() {
    return {
      modalSecond: {
        show: false,
        name: "",
        email: ""
      }
    };
  }
});
</script>