<template>
    <button class="g-button"
            @click="$emit('click')"
            :class="{[`icon-${iconPosition}`]:true}">

        <g-icon v-if="icon && !loading"
                class="icon"
                :name="icon"></g-icon>

        <g-icon v-if="loading"
                class="icon loading"
                name="loading"></g-icon>

        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>
<script>

import Icon from './icon'

export default {
  name: "GuluButton",
//   props:['icon','iconPosition']
  components:{
    'g-icon':Icon
  },
  props:{
      icon:{},
      loading:{
        type:Boolean,
        default:false
      },
      iconPosition:{
          type:String,
          default:'left',
          validator(value){
              return value === 'left' || value === 'right'
          }
      }
  }
};
</script>
<style lang="scss">
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.g-button {
  font-size: var(--font-size);
  height: var(--button-height);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background: var(--button-bg);
  display: inline-flex;
  justify-content: center;
  align-items: center;
  vertical-align: middle;
  cursor: pointer;
  &:hover {
    border-color: var(--border-color-hover);
  }
  &:active {
    background-color: var(--button-active-bg);
  }
  &:focus {
    outline: none;
  }
  > .content {
    order: 2;
  }
  > .icon {
    order: 1;
    margin-right: 0.1em;
  }
  &.icon-right {
    > .content {
      order: 1;
    }
    > .icon {
      order: 2;
      margin-right: 0;
      margin-left: 0.1em;
    }
  }
  .loading {
    animation: spin 2s infinite linear;
  }
}
</style>

