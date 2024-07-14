<template>
  <QBtn
    :no-caps="true"
    :ripple="ripple"
    :color="color"
    :text-color="computedTextColor"
    :unelevated="unelevated"
    v-bind="$attrs"
  >
    <slot />
  </QBtn>
</template>

<script>

import { QBtn } from 'quasar';

export default {
  name: 'ABtn',
  extends: QBtn,
  props: {
    ripple: {
      type: Boolean,
      default: false,
    },
    color: {
      type: String,
      default: 'greyed',
    },
    textColor: {
      type: String,
      default: '',
    },
    unelevated: {
      type: Boolean,
      default: true,
    },
  },
  computed: {
    computedTextColor() {
      if (this.textColor) {
        return this.textColor;
      }
      if (this.color === 'greyed') {
        return this.$q.dark.isActive ? 'white' : 'black';
      }
      return undefined;
    },
  },
};
</script>
