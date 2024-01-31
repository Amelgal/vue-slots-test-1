<script>
import ShowModal from "@/components/Modal.vue";
import {shareLog} from "@/assets/js/api.js";

export default {
  name: 'App',
  components: {ShowModal},
  props: {},
  setup() {
    return {}
  },
  data() {
    return {
      openModal1: false,
      openModal2: false,
      openModal3: false,
      modalAgreeText: '',
    }
  },
  AGREE_TEXT: 'understand',
  computed: {
    agreeTextHandler() {
      return this.modalAgreeText !== this.$options.AGREE_TEXT;
    },
  },
  watch: {
    openModal1(){
      this.modalAgreeText = '';
    },
    openModal2(){
      this.modalAgreeText = '';
    },
    openModal3(){
      this.modalAgreeText = '';
    },
  },
  methods: {
    shareLog,
    ok1() {
      this.openModal1 = false;
    },
    ok2() {
      this.openModal2 = false;
    },
    ok3() {
      shareLog();
      this.openModal3 = false;
    },
    close1() {
      this.openModal1 = false;
    },
    close2() {
      this.openModal2 = false;
    },
    close3() {
      this.openModal3 = false;
    },
  },
  mounted() {
  },
  created() {
  },
}
</script>

<template>
  <section>
    <!-- Trigger/Open The Modal -->
    <button id="myBtnFirst" @click="openModal1 = true">Open first Modal</button>
    <button id="myBtnSecond" @click="openModal2 = true">Open second Modal</button>
    <button id="myBtnThird" @click="openModal3 = true">Open third Modal</button>
  </section>


  <show-modal :is-open="openModal1" @ok="ok1" @close="close1">
    <template #body>
      <p>Some text in the First Modal</p>
    </template>
  </show-modal>


  <show-modal :is-open="openModal2" @ok="ok2" @close="close2">

    <template #body>
      <p>Some text in the Second Modal</p>
    </template>

    <template #footer="{ok: modalOk, close: modalClose}">
      <input v-model="modalAgreeText" type="text" :placeholder="$options.AGREE_TEXT">

      <button id="okBtn"
              :disabled="agreeTextHandler"
              :class="{'bg-gray-400 cursor-not-allowed': agreeTextHandler}"
              @click="modalOk"
      >
        Ok
      </button>
      <button @click="modalClose">Close</button>
    </template>
  </show-modal>


  <show-modal :is-open="openModal3" @ok="ok3" @close="close3">
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
