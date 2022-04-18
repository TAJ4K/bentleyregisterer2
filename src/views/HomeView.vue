<template>
  <div class="home">
    <div>
      <h2>Launch Options</h2>
      <form v-on:submit.prevent="launchScript()">
      <div class="builder">
        <option value=""></option>
      </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { launch } from "../script/register";

export default defineComponent({
  methods: {
    launchScript() {
      launch();
    },
  },
});
</script>
