<template>
    <fieldset class="user-info" v-on:do-validate="validate">
        <legend><h4>Информация о пользователе</h4></legend>

        <!-- Фамилия -->
        <label>
            <span>Фамилия<em>*</em></span>
            <span class="validate-message" v-if="validate_warnings.lastName">{{ validate_warnings.lastName }}</span>
            <input type="text" v-model="lastName" required>
        </label>

        <!-- Имя -->
        <label>
            <span>Имя<em>*</em></span>
            <span class="validate-message" v-if="validate_warnings.firstName">{{ validate_warnings.firstName }}</span>
            <input type="text" v-model="firstName" required>
        </label>

        <!-- Отчество -->
        <label>
            <span>Отчество</span>
            <input type="text" v-model="middleName">
        </label>

        <!-- Дата рождения -->
        <label>
            <span>Дата рождения<em>*</em></span>
            <span class="validate-message">{{ validate_warnings.dob }}</span>
            <input type="date" v-model="dob" required>
        </label>

        <!-- Телефон -->
        <label>
            <span>Телефон<em>*</em></span>
            <span class="validate-message">{{ validate_warnings.phone }}</span>
            <input type="number" v-model="phone" maxlength="11" required>
        </label>

        <!-- Пол -->
        <label>
            <span>Пол</span>
            <select v-model="genderModel">
                <option disabled selected>Выберите один из вариантов</option>
                <option v-for="(item, index) in genderList" v-bind:value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <!-- Группа клиентов -->
        <label>
            <span>Группа клиентов<em>*</em></span>
            <span class="validate-message" v-if="validate_warnings.clientsGroupModel">{{ validate_warnings.clientsGroupModel }}</span>
            <select v-model="clientsGroupModel" multiple required>
                <option disabled selected>Выберите один или несколько вариантов</option>
                <option v-for="(item, index) in clientsGroupList" v-bind:value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <!-- Лечащий врач -->
        <label>
            <span>Лечащий врач</span>
            <select v-model="doctorModel">
                <option disabled selected>Выберите один из вариантов</option>
                <option v-for="(item, index) in doctorList" v-bind:value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <!-- Не отправлять СМС -->
        <label>
            <div>
                <input type="checkbox" v-model="isDontSendSMS"><span>Не отправлять СМС</span>
            </div>
        </label>

    </fieldset>
</template>


<script>
    export default {
        name: 'P1_User',
        data() {
            return {
                clientsGroupList: ['VIP', 'Проблемные', 'ОМС'],
                genderList: ['Женский', 'Мужской', 'Не указан'],
                doctorList: ['Иванов', 'Захаров', 'Чернышева'],


                lastName: '',
                firstName: '',
                middleName: '',
                dob: '',
                phone: '',
                genderModel: null,
                clientsGroupModel: [],
                doctorModel: null,
                isDontSendSMS: false,

                // массив сообщений валидации
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
                    lastName: '',
                    firstName: '',
                    dob: '',
                    phone: '',
                    clientsGroupModel: ''
                }

                // валидация фамилии
                if (!this.lastName.length) {
                    this.validate_warnings.lastName = text_not_filled;
                    isValidate = false;
                }

                // валидация имени
                if (!this.firstName.length) {
                    this.validate_warnings.firstName = text_not_filled;
                    isValidate = false;
                }

                // валидация даты рождения
                if (!this.dob.length) {
                    this.validate_warnings.dob = text_not_filled;
                    isValidate = false;
                }

                // валидация телефона
                if (this.phone[0] !== '7') {
                    this.validate_warnings.phone = 'Номер должен начинаться с 7';
                    isValidate = false;
                }

                if (this.phone.length !== 11) {
                    this.validate_warnings.phone = 'Номер телефона состоит из 11 символов';
                    isValidate = false;
                }

                // валидация группы клиентов
                if (!this.clientsGroupModel.length) {
                    this.validate_warnings.clientsGroupModel = 'Не выбрана группа клиентов'
                    isValidate = false;
                }

                return isValidate;
            }
        }
    }
</script>