<script setup>
import { computed } from 'vue';
import { Link } from '@inertiajs/vue3';

const props = defineProps({
    href: String,
    active: Boolean,
});

const classes = computed(() => {
    return props.active
        ? 'nav-link active font-weight-bolder'
        : 'nav-link';
});
</script>

<template>
  <li class="nav-item">
    <Link :href="href" :class="classes">
      <slot></slot>
    </Link>
  </li>
</template>