<template>
  <button
    :type="type"
    data-testid="submit_button"
    :disabled="disabled"
    :class="computedClass"
    @click="onClick"
  >
    <fluent-icon v-if="!!iconClass" :icon="iconClass" class="icon" />
    <span>{{ buttonText }}</span>
    <spinner v-if="loading" />
  </button>
</template>

<script>
import Spinner from 'shared/components/Spinner';

export default {
  components: {
    Spinner,
  },
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
    buttonText: {
      type: String,
      default: '',
    },
    buttonClass: {
      type: String,
      default: '',
    },
    iconClass: {
      type: String,
      default: '',
    },
    type: {
      type: String,
      default: 'submit',
    },
  },
  computed: {
    computedClass() {
      return `button nice ${this.buttonClass || ' '}`;
    },
  },
  methods: {
    onClick() {
      this.$emit('click');
    },
  },
};
</script>
<style lang="scss" scoped>
button:disabled {
  opacity: 1;
  background-color: var(--grey-light);
  span {
    color: var(--grey-dark);
  }

  &:hover {
    background-color: var(--grey-light);
  }
}
button {
  background-color: #7423D9;
  &:hover {
    background-color: #7423D9;
  }
}
</style>
