<script>
import ShowModal from "@/components/Modal.vue";
import {shareLog} from "@/assets/js/api.js";

export default {
  name: 'App',
  components: {ShowModal},
  data() {
    return {
      modalAgreeText: '',
    }
  },
  AGREE_TEXT: 'understand',
  computed: {
    agreeTextHandler() {
      return this.modalAgreeText !== this.$options.AGREE_TEXT;
    },
  },
  methods: {
    async learnVue() {
      const popup = await this.$refs.popup.open();
      console.log(popup);

      if (popup) {
        shareLog();
      }

      this.modalAgreeText = '';
    }
  }
}
</script>

<template>
  <section>
    <!-- Trigger/Open The Modal -->
    <button id="myBtnThird" @click="learnVue">Learn Vue</button>
  </section>

  <show-modal ref="popup">
    <template #body>
      <p>Some text in the Third Modal</p>
    </template>

    <template #footer="{ok: modalOk, close: modalClose}">
      <input v-model="modalAgreeText" type="text" :placeholder="$options.AGREE_TEXT">

      <button id="okBtn"
              :disabled="agreeTextHandler"
              :class="{'bg-gray-400 cursor-not-allowed': agreeTextHandler}"
              @click="modalOk"
      >
        Send
      </button>
      <button @click="modalClose">Close</button>
    </template>
  </show-modal>
</template>

<style scoped>
/* Add Animation */
@keyframes animatetop {
  from {
    top: -300px;
    opacity: 0
  }
  to {
    top: 0;
    opacity: 1
  }
}
</style>
