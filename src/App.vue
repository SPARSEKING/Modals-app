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
          <button
            @click="modalSecond.show = !modalSecond.show"
            class="btn btnPrimary"
          >
            Show modal with form
          </button>
          <modals
            v-show="modalSecond.show"
            title="Modal with form"
            @close="modalSecond.show = false"
          >
            <template v-slot:body>
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
          </modals>
        </div>
      </section>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import modals from "@/components/Modal.vue";
import { App } from "./App";

export default defineComponent({
  name: "App",
  components: {
    modals
  },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: "",
        email: ""
      }
    } as App;
  }
});
</script>
