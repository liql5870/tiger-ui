<template>
<!--  button按钮，绑定classes样式-->
  <button class="tiger-button" :class=" classes" :disabled="disabled">
    <span v-if="loading" class="tiger-loadingIndicator"></span>
    <slot/>
  </button>

</template>

<script setup lang='ts'>

import {computed, defineProps} from 'vue';

const props = defineProps({
  theme: {
    type: String,
    default: 'button'
  },
  size: {
    type: String,
    default: 'normal'
  },
  level: {
    type: String,
    default: 'normal'
  },
  disabled: {
    type: Boolean,
    default:false
  },
  loading: {
    type: Boolean,
    default: false
  }
});

const classes = computed(() => {
  return {
    [`tiger-theme-${props.theme}`]: props.theme,
    [`tiger-size-${props.size}`]: props.size,
    [`tiger-level-${props.level}`]: props.level
  };

});
</script>

<style lang='scss'>

$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
$red: red;
$grey: grey;

.tiger-button {
  box-sizing: border-box;
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  transition: background 250ms;

  & + & {
    margin-left: 8px;
  }

  &:hover,
  &:focus {
    color: $blue;
    border-color: $blue;
  }

  &:focus {
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  &.tiger-theme-link {
    border-color: transparent;
    box-shadow: none;
    color: $blue;

    &:hover,
    &:focus {
      color: lighten($blue, 10%);
    }
  }

  &.tiger-theme-text {
    border-color: transparent;
    box-shadow: none;
    color: inherit;

    &:hover,
    &:focus {
      background: darken(white, 5%);
    }
  }

  &.tiger-size-big {
    font-size: 24px;
    height: 48px;
    padding: 0 16px;
  }

  &.tiger-size-small {
    font-size: 12px;
    height: 20px;
    padding: 0 4px;
  }

  &.tiger-theme-button {
    &.tiger-level-main {
      background: $blue;
      color: white;
      border-color: $blue;

      &:hover,
      &:focus {
        background: darken($blue, 10%);
        border-color: darken($blue, 10%);
      }
    }

    &.tiger-level-danger {
      background: $red;
      border-color: $red;
      color: white;

      &:hover,
      &:focus {
        background: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }

  &.tiger-theme-link {
    &.tiger-level-danger {
      color: $red;

      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }

  &.tiger-theme-text {
    &.tiger-level-main {
      color: $blue;

      &:hover,
      &:focus {
        color: darken($blue, 10%);
      }
    }

    &.tiger-level-danger {
      color: $red;

      &:hover,
      &:focus {
        color: darken($red, 10%);
      }
    }
  }

  &.tiger-theme-button {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;

      &:hover {
        border-color: $grey;
      }
    }
  }

  &.tiger-theme-link, &.tiger-theme-text {
    &[disabled] {
      cursor: not-allowed;
      color: $grey;
    }
  }

  > .tiger-loadingIndicator {
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    border-radius: 8px;
    border-color: $blue $blue $blue transparent;
    border-style: solid;
    border-width: 2px;
    animation: tiger-spin 1s infinite linear;
  }
}

@keyframes tiger-spin {
  0% {
    transform: rotate(0deg)
  }
  100% {
    transform: rotate(360deg)
  }

}
</style>
