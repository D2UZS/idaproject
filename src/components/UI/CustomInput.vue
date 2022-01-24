<template>
  <input
    :value="modelValue"
    @input="updateInput"
    @blur="validationInput"
    class="custom-input"
    type="text"
    autocomplete="off"
  />
</template>

<script>
export default {
  name: "custom-input",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
    validationInput(event) {
      if (!event.target._value) {
        event.target.classList.add("custom-input--error");
      } else {
        event.target.classList.remove("custom-input--error");
      }
    },
  },
};
</script>

<style scoped lang="scss">
.custom-input {
  width: 100%;
  padding: {
    top: 10px;
    right: 16px;
    bottom: 11px;
    left: 16px;
  }

  font-size: 12px;
  line-height: 15px;
  color: var(--main-color);

  background-color: var(--background-color);
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;

  &::placeholder {
    color: var(--grey-color);
  }

  &:focus {
    outline: 1px solid var(--grey-color);
  }

  &--error {
    outline: 1px solid var(--warning-color);
    &:focus {
      outline: 1px solid var(--warning-color);
    }
  }
}
</style>