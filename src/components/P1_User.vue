<template>
    <fieldset class="form-container-item">
        <legend>Информация о пользователе</legend>

        <label>
            <span>Фамилия<em>*</em></span>
            <input type="text" v-model="lastName" required>
        </label>

        <label>
            <span>Имя<em>*</em></span>
            <input type="text" v-model="firstName" required>
        </label>

        <label>
            <span>Отчество</span>
            <input type="text" v-model="middleName">
        </label>

        <label>
            <span>Дата рождения<em>*</em></span>
            <input type="date" v-model="dob" required>
        </label>

        <label>
            <span>Телефон<em>*</em></span>
            <input type="number" v-model="phone" maxlength="11" required>
        </label>

        <label>
            <span>Пол</span>
            <select v-model="genderModel">
                <option disabled>Выберите один из вариантов</option>
                <option v-for="(item, index) in genders" v-bind:value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <label>
            <span>Группа клиентов<em>*</em></span>
            <select v-model="clientsGroupModel" multiple required>
                <option disabled>Выберите один или несколько вариантов</option>
                <option v-for="(clGroup, index) in clientsGroups" v-bind:value="index" :key="index">
                    {{ clGroup }}
                </option>
            </select>
        </label>

        <label>
            <span>Лечащий врач</span>
            <select v-model="doctorModel">
                <option disabled>Выберите один из вариантов</option>
                <option v-for="(item, index) in doctors" v-bind:value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <label>
            <div>
                <input type="checkbox" v-model="isDontSendSMS" id="isDontSendSMS"><span>Не отправлять СМС</span>
            </div>
        </label>

    </fieldset>
</template>



<script>
    let default_genders = ['Женский', 'Мужской', 'Не указан'];
    let default_clients_groups = ['VIP', 'Проблемные', 'ОМС'];
    let default_doctors = ['Иванов', 'Захаров', 'Чернышева'];

    export default {
        name: 'P1_User',
        props: {
            lastName: String,
            firstName: String,
            middleName: String,
            dob: Date,
            phone: String,
            genders: Array,
            genderModel: Number || null,
            clientsGroups: Array,
            clientsGroupModel: Array || null,
            doctors: Array,
            doctorModel: Number || null,
            isDontSendSMS: Boolean
        },
        created: function () {
            this.genderModel = null;
            this.clientsGroupModel = [];
            this.doctorModel = null;

            this.genders = default_genders;
            this.clientsGroups = default_clients_groups;
            this.doctors = default_doctors;
        }
    }
</script>