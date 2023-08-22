<template>
  <div :id="$style.app">
    <ApartmentsList :items="apartments" />
  </div>
</template>

<script>
import ApartmentsList from './components/apartment/ApertmentsList.vue'
import apartments from './components/apartment/apartments'

export default {
  name: 'App',
  components: {
    ApartmentsList
  },
  data() {
    return {
      apartments,
      apartment: {
        id: "ljhbslhafbljHSBF;KJB",
        title: "lorem nskjnkjadnlk",
        descr: "Роскошные апартаменты в скайндинавском стиле с панорамным видом на реку и бесплатным Wi-Fi.",
        price: 2032,
        rating: 4.7,
        location: {
          city: "Sassnitz"
        },
        owner: {
          name: "Ellen",
          phone: "1234654",
          email: "ownermail@post.com"
        }
      }
    }
  },
}
</script>

<style module>
#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
