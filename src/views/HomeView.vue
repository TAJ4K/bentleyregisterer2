<template>
  <div class="home">
    <div>
      <h2>Launch Options</h2>
      <form v-on:submit.prevent="launchScript()">
        <div id="semesterSelector">
          <div class="semesterOption">Latest</div>
          <div class="semesterOption">Build</div>
          <div class="builder" v-if="buildSemester">
            <option value=""></option>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { launch } from "../script/register";

export default defineComponent({
  data() {
    return {
      buildSemester: false,
    };
  },
  methods: {
    launchScript() {
      launch();
    },
  },
});
</script>

<style scoped>
.semesterOption {
  width: 8em;
  height: 3em;
  border-radius: 10px;
}
</style>
