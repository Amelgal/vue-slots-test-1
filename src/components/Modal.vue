<script>
export default {
  name: "ShowModal",
  props: {
    isOpen: {
      type: Boolean,
      required: false,
      default: false,
    }
  },
  emits: {
    'close': null,
    'ok': null
  },
  methods: {
    close() {
      this.$emit('close');
    },
    ok() {
      this.$emit('ok');
    },
  },
}
</script>

<template>
  <div id="myModal" class="modal"
       :class="{
      'hidden': !isOpen,
    }"
       @click="close"
  >
    <!-- Modal content -->
    <div class="modal-content" @click.stop>
      <div class="modal-header">
        <span class="close" @click="close">&times;</span>
        <h2>Modal Header</h2>
      </div>

      <slot name="body" class="modal-body"></slot>

      <slot name="footer" class="modal-footer" :close="close" :ok="ok">
        <h3>Modal Footer</h3>
        <button id="closeBtn" @click="close">Close</button>
        <button id="okBtn" @click="ok">Ok</button>
      </slot>
    </div>
  </div>
</template>

<style>
.hidden {
  display: none;
}

/* The Modal (background) */
.modal {
  position: fixed; /* Stay in place */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 15% auto; /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 80%; /* Could be more or less, depending on screen size */
}

/* The Close Button */
.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

/* Modal Header */
.modal-header {
  padding: 2px 16px;
  background-color: #5cb85c;
  color: white;
}

/* Modal Body */
.modal-body {
  padding: 2px 16px;
}

/* Modal Footer */
.modal-footer {
  padding: 2px 16px;
  background-color: #5cb85c;
  color: white;
}

/* Modal Content */
.modal-content {
  position: relative;
  background-color: #fefefe;
  margin: auto;
  padding: 0;
  border: 1px solid #888;
  width: 80%;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  animation-name: animatetop;
  animation-duration: 0.4s
}

</style>