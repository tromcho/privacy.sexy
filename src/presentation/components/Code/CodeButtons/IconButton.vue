<template>
  <button class="button" @click="onClicked">
    <font-awesome-icon
      class="button__icon"
      :icon="[iconPrefix, iconName]" size="2x"  />
    <div class="button__text">{{text}}</div>
  </button>
</template>

<script lang="ts">
import {
  Component, Prop, Emit, Vue,
} from 'vue-property-decorator';

@Component
export default class IconButton extends Vue {
  @Prop() public text!: number;

  @Prop() public iconPrefix!: string;

  @Prop() public iconName!: string;

  @Emit('click') public onClicked() { /* do nothing except firing event */ }
}
</script>

<style scoped lang="scss">
@use "@/presentation/assets/styles/main" as *;

.button {
  display: flex;
  flex-direction: column;
  align-items: center;

  background-color: $color-secondary;
  color: $color-on-secondary;

  border: none;
  padding:20px;
  transition-duration: 0.4s;
  overflow: hidden;
  box-shadow: 0 3px 9px $color-primary-darkest;
  border-radius: 4px;

  @include clickable;

  width: 10%;
  min-width: 90px;
  @include hover-or-touch {
    background: $color-surface;
    box-shadow: 0px 2px 10px 5px $color-secondary;
  }
  @include hover-or-touch('>&__text') {
    display: block;
  }
  @include hover-or-touch('>&__icon') {
    display: none;
  }
  &__text {
    display: none;
    font-family: $font-artistic;
    font-size: 1.5em;
    color: $color-primary;
    font-weight: 500;
    line-height: 1.1;
    @include hover-or-touch {
      display: block;
    }
  }
}
</style>
