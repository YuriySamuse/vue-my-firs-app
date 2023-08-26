<template>
  <div id="app">
    <h2>Input: {{ text }}</h2>
    <Container>
      <ApartmentsFilterForm class="apartment-filter" @submit="logger" />

    </Container>
    <ApartmentsList :items="apartments">
      <!-- <template v-slot:title>New Title</template> -->
      <template v-slot:apartment="{ apartment }">
        <ApartmentsItem :key="apartment.id" :descr="apartment.descr" :rating="apartment.rating" :imgSrc="apartment.imgUrl"
          :price="apartment.price" @click="handleItemClick" />
      </template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentsList from './components/apartment/ApertmentsList.vue'
import ApartmentsItem from './components/apartment/ApartmentsItem.vue';
import apartments from './components/apartment/apartments'
import ApartmentsFilterForm from './components/apartment/ApartmentFilterForm.vue'
import Container from './components/shared/Container.vue'

export default {
  name: 'App',
  components: {
    ApartmentsList,
    ApartmentsItem,
    ApartmentsFilterForm,
    Container
  },
  data() {
    return {
      text: '',
      apartments,
    }
  },
  methods: {
    handleItemClick() {
      console.log('item click');
    },
    logger(value) {
      console.log(value, '----form value');
    },

  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.apartment-filter {
  margin-bottom: 40px;
}
</style>
