<template>
  <div class="container">
    <h2 class="title">LoadingIndicator</h2>
    <form class="content">
<<<<<<< HEAD
      <span @click="setLoading()">Global LoadingIndicator</span>
      <span @click="setLoading()">LoadingIndicator</span>
=======
      <span @click="setLoading('global')">
        Global LoadingIndicator
      </span>
      <span @click="setLoading('local')">LoadingIndicator</span>
>>>>>>> 4611b0f (tech : loading sample)
      <div class="section">
        <!-- <LoadingIndicatorGlobal v-if="state.isGlobalLoading" />
        <LoadingIndicator v-if="state.isLoading" /> -->
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue'
import { definePageMeta } from '#imports'
import LoadingIndicatorGlobal from '@/components/base/LoadingIndicatorGlobal.vue'
import LoadingIndicator from '@/components/base/LoadingIndicator.vue'

definePageMeta({
  layout: 'sub',
})

export default defineComponent({
  components: {
    LoadingIndicatorGlobal,
    LoadingIndicator,
  },
  setup() {
    const isGlobalLoading = ref(false)
    const isLoading = ref(false)

    const setLoading =(type = 'local')=> {
      type === 'local' ?
        isLoading.value = !isLoading.value
        :
        isGlobalLoading.value = !isGlobalLoading.value

    }

    return { isGlobalLoading, isLoading, setLoading }
  },
})
</script>

<style lang="scss" scoped>
@import '@/assets/styles/abstracts/variables.scss';
@import '@/assets/styles/abstracts/functions.scss';
@import '@/assets/styles/abstracts/mixin.scss';

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: auto;
  padding: 120px 24px;
  width: 100%;
  max-width: 960px;
}

.title {
  @include text-style($text-heading2-bold);
}

.content {
  display: flex;
  gap: 8px;
  width: 100%;

  .section {
    margin-top: 24px;
    border-top: 1px solid $color-text-5;
  }

  span {
    padding: 8px;
    border: 1px solid $color-text-5;
    border-radius: 8px;
    margin-top: 8px;
    color: $color-text-6;
    cursor: pointer;
  }
}
</style>
