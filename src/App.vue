<template>
  <div id="app">
    <h1 class="align-center">Новый клиент</h1>

    <div class="form-container">
      <P1_User></P1_User>
    </div>

  </div>
</template>

<script>
import P1_User from "@/components/P1_User";

export default {
  name: 'App',
  components: {
    P1_User
  },
}
</script>