<template>
  <div class="home">
    <section>
      <h1>All Destinations</h1>
      <div class="destinations">
        <div v-for="destination in destinations" :key="destination.name">
          <router-link :to="destination.slug">
            <h2>{{ destination.name }}</h2>
          </router-link>

          <figure>
            <router-link :to="destination.name">
              <img
                :src="require(`@/assets/${destination.image}`)"
                width="300px"
                height="200px"
              />
            </router-link>
          </figure>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import store from "@/store.js";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>

<style scoped>
.home {
  max-width: 1400px;
  margin: 0 auto;
}

.destinations {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>
