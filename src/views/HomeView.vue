<script setup>
import { ref } from 'vue'
import { Minus, Plus, RotateCcw } from '@lucide/vue'

const count = ref(0)
</script>

<template>
  <section>
    <p class="eyebrow">12 / THE STUDIO NOTEBOOK</p>
    <h1>A little Vue,<br />ready for the web.</h1>
    <p class="intro">Week 12. A small experiment in building and shipping.</p>
    <div class="counter-panel">
      <div class="panel-heading">
        <h2>The counter</h2>
        <button class="icon-button" type="button" aria-label="Reset counter" title="Reset counter" @click="count = 0">
          <RotateCcw :size="18" />
        </button>
      </div>
      <div class="counter-controls">
        <button class="icon-button" type="button" aria-label="Decrease counter" title="Decrease counter" @click="count--">
          <Minus :size="20" />
        </button>
        <output aria-live="polite" aria-label="Count">{{ count }}</output>
        <button class="icon-button primary" type="button" aria-label="Increase counter" title="Increase counter" @click="count++">
          <Plus :size="20" />
        </button>
      </div>
    </div>
  </section>
</template>