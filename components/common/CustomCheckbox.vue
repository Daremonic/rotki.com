<script setup lang="ts">
withDefaults(
  defineProps<{
    id?: string;
    modelValue: boolean;
  }>(),
  {
    id: '',
  },
);

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void;
}>();

function update(checked: boolean) {
  emit('update:modelValue', checked);
}
</script>

<template>
  <div :class="$style.checkbox">
    <input
      :id="id"
      :modelValue="modelValue"
      type="checkbox"
      @click="update(!modelValue)"
    />
    <label
      :class="$style.label"
      :for="id"
    >
      <slot />
    </label>
  </div>
</template>

<style lang="scss" module>
.checkbox {
  @apply flex flex-row items-center;

  font-size: 15px;
  line-height: 18px;
  margin-top: 16px;

  input {
    @apply text-rui-primary-darker;
  }
}

.label {
  @apply ml-4;
}
</style>
