<template>
  <div id="app">
      <div class="app-wrapper">
              <h1 class="align-center">Новый клиент</h1>

          <div class="form-container">
              <P1_User></P1_User>
              <P1_UserAddress></P1_UserAddress>
          </div>
      </div>
  </div>
</template>

<script>
import P1_User from "@/components/P1_User";
import P1_UserAddress from "@/components/P1_UserAddress";

export default {
  name: 'App',
  components: {
    P1_User,
    P1_UserAddress
  },
}
</script>