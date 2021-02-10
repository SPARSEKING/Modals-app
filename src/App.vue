<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <!-- first modal -->
          <button @click="modalFirst = !modalFirst" class="btn btnPrimary">
            Show First modal
          </button>
          <modals
            v-show="modalFirst"
            title="First modal"
            @close="modalFirst = false"
          >
            <template v-slot:body>
              <p>It's my first modal window</p>
              <button @click="modalFirst = !modalFirst" class="btn btnPrimary">
                Well done!
              </button>
            </template>
          </modals>
          <!-- Second modal -->
          <button @click="show = !show" class="btn btnPrimary">
            Show modal with form
          </button>
          <modals v-show="show" title="Modal with form" @close="show = false">
            <template v-slot:body>
              <forms></forms>
            </template>
          </modals>
        </div>
      </section>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import modals from "@/components/Modal.vue";
import forms from "@/components/Form.vue";
import { App } from "./App";

export default defineComponent({
  name: "App",
  components: {
    modals,
    forms
  },
  data() {
    return {
      modalFirst: false,
      show: false
    } as App;
  }
});
</script>
