<template>
  <div>
    <section class="destinations">
      <h1>
        {{ destination.name }}
      </h1>
      <div class="destination-details">
        <img
          :src="require(`@/assets/${destination.image}`)"
          :alt="destination.name"
        />
        <p>{{ destination.description }}</p>
      </div>
    </section>

    <section class="experiences">
      <h2>Top experiences in {{ destination.name }}</h2>
      <div class="cards">
        <div
          class="card"
          v-for="experience in destination.experiences"
          :key="experience.slug"
        >
          <img :src="require(`@/assets/${experience.image}`)" />
          <span class="cart__text">
            {{ experience.name }}
          </span>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import store from "@/store";
export default {
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  data() {
    return {};
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug === this.slug
      );
    },
  },
};
</script>

<style scoped>
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}
.destination-details {
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}

.cards {
  display: flex;
  justify-content: space-between;
}
.cards img {
  max-height: 200px;
}
.card {
  padding: 0 20px;
  position: relative;
}
.card__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 25px;
  font-weight: bold;
  text-decoration: none;
}
</style>
