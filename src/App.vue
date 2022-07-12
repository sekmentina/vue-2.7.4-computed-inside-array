<script setup>
import { ref, reactive, computed, watch } from 'vue';

const cmp = computed(() => 0);

const rctv = reactive({
  cmpArr: [cmp],
});

const obj = {
  cmpArr: [cmp],
};

const rctvWithRef = reactive({
  refArr: [ref(0)],
});

//  RangeError: Maximum call stack size exceeded at [Symbol.hasInstance] (<anonymous>) at _traverse (vue.runtime.esm.js:1145:9)
// watch(rctv, () => {});

// vue-query use this method to observe queryKey
// watch(() => obj, () => {}, { deep: true });
//  RangeError: Maximum call stack size exceeded at [Symbol.hasInstance] (<anonymous>) at _traverse (vue.runtime.esm.js:1145:9)

// work well. Seems reactive not unwrap cmoputed inside array.
watch(rctvWithRef, () => {});
</script>

<template>
  <div></div>
</template>
