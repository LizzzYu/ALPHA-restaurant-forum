<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>

    <hr />
    <div
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      class="card mb-3"
      style="max-width: 540px; margin: auto"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img class="card-img" :src="restaurant.image" />
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ restaurant.name }}</h5>
            <span class="badge badge-secondary"
              >收藏數：{{ restaurant.FavoriteCount }}</span
            >
            <p class="card-text">
              {{ restaurant.description }}
            </p>
            <router-link
              :to="{ name: 'restaurant', params: { id: restaurant.id } }"
              class="btn btn-primary mr-2"
            >
              show
            </router-link>
            <button
              v-if="restaurant.isFavorited"
              @click="deleteFavorite(restaurant.id)"
              type="button"
              class="btn btn-danger mr-2"
            >
              移除最愛
            </button>
            <button
              v-else
              @click="addFavorite(restaurant.id)"
              type="button"
              class="btn btn-primary"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import restaurantAPI from '../apis/restaurants';
import usersAPI from '../apis/users';
import { Toast } from '../utils/helpers';
import NavTabs from '../components/NavTabs.vue';

export default {
  name: 'RestaurantsTop',
  components: {
    NavTabs,
  },
  created() {
    this.fetchRestaurantsTop();
  },
  data() {
    return {
      restaurants: [],
    };
  },
  methods: {
    async fetchRestaurantsTop() {
      try {
        const response = await restaurantAPI.getRestaurantTop();
        const { data } = response;
        this.restaurants = data.restaurants;
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法取得人氣餐廳，請稍後再試',
        });
      }
    },
    async addFavorite(restaurantId) {
      try {
        const response = await usersAPI.addFavorite({ restaurantId });
        const { data } = response;

        if (data.status !== 'success') {
          throw new Error(data.message);
        }

        this.restaurants = this.restaurants.map((restaurant) => {
          if (restaurant.id !== restaurantId) {
            return restaurant;
          }
          return {
            ...restaurant,
            isFavorited: true,
            FavoriteCount: restaurant.FavoriteCount + 1,
          };
        });
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法將餐廳加入最愛，請稍後再試',
        });
      }
    },
    async deleteFavorite(restaurantId) {
      try {
        const { data } = await usersAPI.deleteFavorite({ restaurantId });

        if (data.status !== 'success') {
          throw new Error(data.message);
        }

        this.restaurants = this.restaurants.map((restaurant) => {
          if (restaurant.id !== restaurantId) {
            return restaurant;
          }

          return {
            ...restaurant,
            isFavorited: false,
            FavoriteCount: restaurant.FavoriteCount - 1,
          };
        });
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法將餐廳刪除最愛，請稍後再試',
        });
      }
    },
  },
};
</script>
