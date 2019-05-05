<template>
  <transition name="fade">
    <div class="message-container" v-if="show">
      <div class="ui message" :class="notifType">
        <i class="close icon" @click="hide"></i>
        <div class="header">{{ notifHeader }}</div>
        <slot></slot>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    notifType: {
      type: String,
      default: "info",
      validator: value =>
        ["warning", "info", "positive", "success", "negative", "error"].indexOf(
          value
        ) !== -1
    },

    notifHeader: {
      type: String,
      default: "Information"
    }
  },

  data() {
    return {
      show: true
    };
  },

  methods: {
    hide() {
      this.show = !this.show;
    }
  }
};
</script>

<style >
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.message-container {
  margin: 20px 0;
}
</style>

