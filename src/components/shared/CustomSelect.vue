<template>
    <select v-on:input="inputlisteners" class="custom-select">
        <option v-for="item in formatedItems" :key="item.value" :value="item.value">
            {{ item.label }}</option>
    </select>
</template>

<script>
export default {
    name: 'CustomSelect',
    props: {
        items: {
            type: Array,
            requaired: true,
        }
    },
    methods: {
        inputlisteners(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    },
    computed: {
        formatedItems() {
            return this.items.map(item => {
                return typeof item === 'object'
                    ? item
                    : { value: item, label: item }
            })
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../../assets/scss/variables.scss';

.custom-select {
    height: 40px;
    border: 2px solid $main-color;
    font-size: 18px;
    outline: none;
    padding: 8px 15px;
    cursor: pointer;
    display: inline-block;
}
</style>