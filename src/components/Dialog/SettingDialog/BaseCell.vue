<template>
  <QCardActions class="q-px-md bg-surface" :class="props.class">
    <div>{{ title }}</div>
    <div :aria-label="description">
      <QIcon name="help_outline" size="sm" class="help-hover-icon">
        <QTooltip
          :delay="500"
          anchor="center right"
          self="center left"
          transition-show="jump-right"
          transition-hide="jump-left"
        >
          {{ description }}
        </QTooltip>
      </QIcon>
    </div>
    <QSpace />
    <slot />
  </QCardActions>
</template>

<script setup lang="ts">
export type Props = {
  title: string;
  description: string;
  class?: unknown; // 型はquasarの定義を真似ている
};

const props = defineProps<Props>();
</script>

<style scoped lang="scss">
@use "@/styles/visually-hidden" as visually-hidden;
@use "@/styles/colors" as colors;

.help-hover-icon {
  margin-left: 6px;
  color: colors.$display;
  opacity: 0.5;
}
</style>
