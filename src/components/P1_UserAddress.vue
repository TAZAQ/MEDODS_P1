<template>
    <fieldset class="user-address">
        <legend><h4>Адрес</h4></legend>

        <label>
            <span>Индекс</span>
            <input type="text" v-model="postalCode">
        </label>

        <label>
            <span>Страна</span>
            <input type="text" v-model="country">
        </label>

        <label>
            <span>Область</span>
            <input type="text" v-model="region">
        </label>

        <label>
            <span>Город<em>*</em></span>
            <span class="validate-message">{{ validate_warnings.city }}</span>
            <input type="text" v-model="city" required>
        </label>

        <label>
            <span>Улица</span>
            <input type="text" v-model="street">
        </label>

        <label>
            <span>Дом</span>
            <input type="text" v-model="house">
        </label>
    </fieldset>
</template>


<script>
    export default {
        name: 'P1_UserAddress',
        data() {
            return {
                postalCode: '',
                country: '',
                region: '',
                city: '',
                street: '',
                house: '',

                validate_warnings: {}
            }
        },
        methods: {
            validate: function () {
                let text_not_filled = 'Не заполнено';

                // по-умолчанию валидация пройдена
                let isValidate = true;

                // обнуление сообщений
                this.validate_warnings = {
                    city: ''
                }

                // валидация города
                if (!this.city.length) {
                    this.validate_warnings.city = text_not_filled;
                    isValidate = false;
                }

                return isValidate;
            }
        }
    }
</script>