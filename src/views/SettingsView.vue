<template>
  <div class="settings">
    <h1>Settings</h1>
    <form id="login" v-on:submit.prevent="savedata()">
      <input type="text" id="email" placeholder="Email" @change="addUrl()" />
      <div id="appendurl" />
      <input type="text" id="password" placeholder="Password" />
      <input type="submit" value="Save" />
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      typed: false,
    };
  },
  methods: {
    addUrl() {
      const email = document.getElementById("email") as HTMLInputElement;
      const el = document.getElementById("appendurl");
      if (!el || !email) return;

      if (email.value.includes("@") || email.value == "") {
        el.innerHTML = "";
        return;
      }
      const text = "Add @falcon.bentley.edu to your email?";
      el.innerHTML = text;
      el.style.color = "#42b983";
      el.style.cursor = "pointer";
      el.onclick = () => {
        email.value += "@falcon.bentley.edu";
        el.innerHTML = "";
      };
    },
    savedata() {
      const email = document.getElementById("email") as HTMLInputElement;
      const password = document.getElementById("password") as HTMLInputElement;
      if (!email || !password) return;

      const data = {
        email: email.value,
        password: password.value,
      };
      localStorage.setItem("login", btoa(JSON.stringify(data)));
    },
  },
});
</script>

<style>
#login {
  display: flex;
  flex-direction: column;
}

#login > input {
  width: max-content;
  margin: 10px 10px 10px 0;
}

#login > div {
  width: max-content;
}
</style>
