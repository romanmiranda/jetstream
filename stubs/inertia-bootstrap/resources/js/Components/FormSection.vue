<script setup>
import { computed, useSlots } from 'vue';
import SectionTitle from './SectionTitle.vue';

defineEmits(['submitted']);

const hasActions = computed(() => !! useSlots().actions);
</script>

<template>
  <div class="row">
    <div class="col-md-4">
      <SectionTitle>
        <template #title><slot name="title"></slot></template>
        <template #description>
          <span class="small">
            <slot name="description"></slot>
          </span>
        </template>
      </SectionTitle>
    </div>

    <div class="col-md-8">
      <form @submit.prevent="$emit('submitted')">
        <div class="card shadow-sm">
          <div class="card-body">
            <slot name="form"></slot>
          </div>

          <div class="card-footer d-flex justify-content-end" v-if="hasActions">
            <slot name="actions"></slot>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>