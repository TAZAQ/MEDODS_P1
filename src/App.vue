<template>
    <form id="app">
        <h1 class="p-text-center">Новый клиент</h1>

        <div class="app-wrapper">
            <P1_User ref="user_info"></P1_User>
            <P1_UserAddress ref="user_address"></P1_UserAddress>
            <P1_UserDocument ref="user_document"></P1_UserDocument>
        </div>
        <button type="button" @click="validate">Создать</button>

        <!-- Alert -->
        <h4 id="success_message">Клиент создан!</h4>
    </form>
</template>

<script>
import P1_User from "@/components/P1_User";
import P1_UserAddress from "@/components/P1_UserAddress";
import P1_UserDocument from "@/components/P1_UserDocument";

export default {
    name: 'App',
    components: {
      P1_User,
      P1_UserAddress,
      P1_UserDocument
    },
    methods: {
        validate: function () {
            if (this.$refs.user_info.validate() &&
                this.$refs.user_address.validate() &&
                this.$refs.user_document.validate()
            ) {
                let med = document.getElementById('success_message');

                med.style.display = 'block';
                med.innerText = 'Новый клиент успешно создан!';
                setTimeout(
                    function () {
                        med.style.display = 'none';
                    },
                    2000
                )

            }
        }
    }
}
</script>