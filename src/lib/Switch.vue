<template>
  <button class="pineapple-switch" @click="toggle" :class="{ 'pineapple-checked': value }">
    <span></span>
  </button>
</template>
<script lang="ts" setup="props, context">
const props = defineProps<{ value: boolean }>()
const emit = defineEmits<{
  (e: 'update:value', visible: boolean): void;
}>()
const toggle = () => {
  emit("update:value", !props.value);
};
</script>

<style lang="scss" scoped>
@use "sass:math";
$h: 22px;
$h2: $h - 4px;

.pineapple-switch {
  height: $h;
  width: $h * 2;
  border: none;
  background: #bfbfbf;
  border-radius: math.div($h, 2);
  position: relative;

  >span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background: white;
    border-radius: math.div($h2, 2);
    transition: all 250ms;
  }

  &.pineapple-checked {
    background: #1890ff;

    >span {
      left: calc(100% - #{$h2} - 2px);
    }
  }

  &:focus {
    outline: none;
  }

  &:active {
    >span {
      width: $h2 + 4px;
    }
  }

  &.pineapple-checked:active {
    >span {
      width: $h2 + 4px;
      margin-left: -4px;
    }
  }
}
</style>
