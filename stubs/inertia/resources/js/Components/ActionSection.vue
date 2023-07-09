<script setup>
import SectionTitle from './SectionTitle.vue';
</script>

<template>
  <div class="row">
    <div class="col-md-4">
      <SectionTitle>
        <template #title><slot name="title"></slot></template>
        <template #description><slot name="description"></slot></template>
      </SectionTitle>
    </div>

    <div class="col-md-8">
      <div class="card shadow-sm">
        <div class="card-body">
          <slot name="content"></slot>
        </div>
      </div>
    </div>
  </div>
</template>
