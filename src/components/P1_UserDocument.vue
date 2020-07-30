<template>
    <fieldset class="user-document">
        <legend><h4>Документ</h4></legend>

        <!-- Тип документа -->
        <label>
            <span>Тип документа<em>*</em></span>
            <span class="validate-message" v-if="validate_warnings.documentTypeModel">
                {{ validate_warnings.documentTypeModel }}
            </span>
            <select v-model="documentTypeModel" required>
                <option disabled>Выберите один из вариантов</option>
                <option v-for="(item, index) in documentTypeList" :value="index" :key="index">
                    {{ item }}
                </option>
            </select>
        </label>

        <!-- Серия -->
        <label>
            <span>Серия</span>
            <input type="text" :value="serialNumber">
        </label>

        <!-- Номер -->
        <label>
            <span>Номер</span>
            <input type="text" :value="docNumber">
        </label>

        <!-- Кем выдан -->
        <label>
            <span>Кем выдан</span>
            <input type="text" :value="givenBy">
        </label>

        <!-- Дата выдачи -->
        <label>
            <span>Дата выдачи<em>*</em></span>
            <span class="validate-message" v-if="validate_warnings.givenDate">
                {{ validate_warnings.givenDate }}
            </span>
            <input type="date" v-model="givenDate" required>
        </label>


    </fieldset>
</template>




<script>
    export default {
        name: 'P1_UserDocument',
        data() {
            return {
                documentTypeList: ['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
                documentTypeModel: null,
                serialNumber: '',
                docNumber: '',
                givenBy: '',
                givenDate: '',

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
                    documentTypeModel: '',
                    givenDate: ''
                }

                // валидация тип документа
                if (!Number.isInteger(this.documentTypeModel)) {
                    this.validate_warnings.documentTypeModel = text_not_filled;
                    isValidate = false;
                }

                // валидация даты выдачи
                if (!this.givenDate.length) {
                    this.validate_warnings.givenDate = 'Не выбрана дата';
                    isValidate = false;
                }

                return isValidate;
            }
        }
    }
</script>