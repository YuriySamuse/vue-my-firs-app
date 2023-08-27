<template>
  <div id="app">
    <h2>{{ text }}</h2>
    <Container>
      <ApartmentsFilterForm class="apartments-filter" @apartmentFilter="filter" />
    </Container>
    <p v-if="!filteredApartments.length">Ничего не найдено</p>
    <ApartmentsList v-else :items="filteredApartments">
      <template v-slot:apartment="{ apartment }">
        <ApartmentsItem :key="apartment.id" :descr="apartment.descr" :rating="apartment.rating" :imgSrc="apartment.imgUrl"
          :price="apartment.price" />
      </template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentsList from './components/apartment/ApartmentsList'
import ApartmentsItem from './components/apartment/ApartmentsItem'
import apartments from './components/apartment/apartments'
import ApartmentsFilterForm from './components/apartment/ApartmentFilterForm'
import Container from './components/shared/Container'

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
      filters: {
        city: '',
        price: 0
      }
    }
  },
  computed: {
    filteredApartments() {
      // return this.filterByCityName(this.filterByPrice(this.apartments))
      return this.apartments.filter(apartment => {
        return this.isValidCity(apartment)
          && this.isValidPrice(apartment)
      })
    }
  },
  methods: {
    isValidCity(apartment) {
      if (!this.filters.city) {
        return true
      }
      return apartment.location.city === this.filters.city
    },
    isValidPrice(apartment) {
      if (!this.filters.price) {
        return true
      }
      return apartment.price >= this.filters.price
    },
    filter({ city, price }) {
      // console.log(price, city, this.filters, ...arguments);
      this.filters.city = city
      this.filters.price = price
    },
    // filterByCityName(apartments) {
    //   if (!this.filters.city) return apartments

    //   return apartments.filter(apartment => {
    //     return apartment.location.city === this.filters.city
    //   })
    // },
    // filterByPrice(apartments) {
    //   if (!this.filters.price) return apartments

    //   return apartments.filter(apartment => {
    //     // console.log(this.filters.price);

    //     return apartment.price >= this.filters.price
    //   })
    // }
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

.apartments-filter {
  margin-bottom: 40px;
}
</style>