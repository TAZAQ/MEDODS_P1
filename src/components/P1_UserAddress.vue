<template>
    <fieldset class="form-container-item">
        <legend>Адрес</legend>

        <label>
            <span>Индекс</span>
            <input type="text" v-model="postalCode">
        </label>

        <label>
            <span>Страна</span>
            <input type="text" v-model="postalCode">
        </label>

        <label>
            <span>Область</span>
            <input type="text" v-model="postalCode">
        </label>

        <label>
            <span>Город<em>*</em></span>
            <input type="text" v-model="postalCode" required>
        </label>

        <label>
            <span>Улица</span>
            <input type="text" v-model="postalCode">
        </label>

        <label>
            <span>Дом</span>
            <input type="text" v-model="postalCode">
        </label>
    </fieldset>
</template>


<script>
    export default {
        name: 'P1_UserAddress',
        props: {
            postalCode: String,
            country: String,
            region: String,
            city: String,
            street: String,
            house: String
        }
    }
</script>