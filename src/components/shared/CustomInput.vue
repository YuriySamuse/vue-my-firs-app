
<template>
    <input v-on:input="inputlisteners" class="custom-input">
</template>

<script>
export default {
    name: 'CastomInput',
    methods: {
        inputlisteners(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../../assets/scss/variables.scss';

.custom-input {
    min-height: 40px;
    max-width: 220px;
    width: 100%;
    border: 2px solid $main-color;
    font-size: 18px;
    outline: none;
    line-height: inherit;
    padding: 8px 15px;

    &::placeholder {
        color: inherit;
    }
}
</style>
