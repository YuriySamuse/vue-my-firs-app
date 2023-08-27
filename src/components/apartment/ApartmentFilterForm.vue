<template>
    <form class="form" @submit.prevent="handleSubmit">
        <CustomSelect :items="cities" class="form__select" v-model="city" />
        <CustomInput placeholder="Цена, от" v-model="price" />
        <SubmitButton class="form__submit" type="submit">Подбор жилья</SubmitButton>
    </form>
</template>

<script>
import CustomSelect from '../shared/CustomSelect'
import CustomInput from '../shared/CustomInput'
import SubmitButton from '../shared/Button.vue'

export default {
    components: {
        CustomSelect,
        CustomInput,
        SubmitButton
    },
    data() {
        return {
            price: '',
            city: ''
        }
    },
    computed: {
        cities() {
            return [{ value: '', label: 'Город', selected: true }, 'Kyiv', 'Odessa', 'Poltava', 'Kharkiv', 'Dnipro', 'Lviv', 'Kherson', 'Mariupol']
        }
    },
    methods: {
        handleSubmit() {
            this.$emit('apartmentFilter', {
                city: this.city,
                price: this.price
            })
        }
    }
}
</script>

<style lang="scss" scoped>
.form {
    display: flex;

    &__select {
        margin-right: 30px;
    }

    &__submit {
        margin-left: auto;
    }
}
</style>