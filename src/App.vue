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
              <form @submit.prevent="submitSecondForm">
                <label>Name</label>
                <input
                  type="text"
                  @input="e => (modalSecond.name = e.target.value)"
                  :value="modalSecond.name"
                />
                <label>Email</label>
                <input
                  type="email"
                  @input="e => (modalSecond.email = e.target.value)"
                  :value="modalSecond.email"
                />
                <button
                  id="button-second"
                  class="btn btnPrimary"
                  @click="showParam"
                >
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
import modals from "@/components/UI/Modal.vue";
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
      },
      modalValidate: false
    } as App;
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      });
      this.modalSecond.name = "";
      this.modalSecond.email = "";
      this.modalSecond.show = false;
    }
  }
});
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

input {
  width: 400px;
  height: 30px;
  border: 1px solid #999;
  border-radius: 10px;
}

label {
  padding-top: 20px;
}

#button-second {
  width: 200px;
}
</style>
