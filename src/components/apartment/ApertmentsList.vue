<template>
    <Container>
        <div class="apartments-list">
            <ApartmentsItem v-for="{ id, descr, rating, imgUrl, price } in items" :key="id" :descr="descr" :rating="rating"
                :imgSrc="imgUrl" :price="price" class="apartments-list__item" />
        </div>
    </Container>
</template>

<script>
import ApartmentsItem from './ApartmentsItem.vue';
import Container from '../shared/Container'

export default {
    name: "ApertmentsList",
    components: {
        ApartmentsItem,
        Container,
    },
    props: {
        items: Array,
        default: () => []
    }

}
</script>

<style lang="scss" scoped>
.apartments-list {
    display: flex;
    flex-wrap: wrap;
    margin-left: -15px;
    margin-right: -15px;

    &_item {
        margin-bottom: 30px;
    }
}
</style>