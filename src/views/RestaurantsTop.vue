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
import NavTabs from '../components/NavTabs.vue';

const dummyData = {
  restaurants: [
    {
      id: 50,
      name: 'Mossie Bartoletti',
      tel: '(392) 036-9035',
      address: '805 Casper Harbor',
      opening_hours: '08:00',
      description: 'Ut molestias excepturi magni et consequatur.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=16.563720368747315',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: 'Nikolas Schuster',
      tel: '060.512.5232 x374',
      address: '9835 Royal Camp',
      opening_hours: '08:00',
      description: 'Et sit eius aut quo expedita. Fugiat expedita volu',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=32.81392081379772',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: 'Emmalee Dickinson',
      tel: '1-576-548-0668 x43021',
      address: '39939 Katelyn Squares',
      opening_hours: '08:00',
      description: 'Qui recusandae cupiditate et ut voluptates et. Eni',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=5.4245529688122796',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: 'Jerrold Metz',
      tel: '908.229.7303 x79812',
      address: '436 Callie Causeway',
      opening_hours: '08:00',
      description: 'Iste voluptatum aut consequatur pariatur reiciendi',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.828155682682322',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: 'Kamren Brown',
      tel: '(467) 271-7341 x2849',
      address: '372 Doyle Orchard',
      opening_hours: '08:00',
      description: 'Nobis cupiditate veritatis.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=81.22291896392373',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: 'Roselyn McLaughlin',
      tel: '(479) 706-9055 x91343',
      address: '82057 Ettie Throughway',
      opening_hours: '08:00',
      description: 'Porro explicabo quae exercitationem sit laudantium',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=12.401057286026184',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: 'Joy Lowe',
      tel: '1-248-034-2606 x975',
      address: '354 Dashawn Cove',
      opening_hours: '08:00',
      description: 'Voluptate unde qui nulla. Quidem rerum quasi ratio',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.304819817476112',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: 'Bernard Casper DDS',
      tel: '1-267-747-6873 x6348',
      address: '0268 Dickinson Falls',
      opening_hours: '08:00',
      description: 'repudiandae',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=87.07205981616009',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: 'Maiya Flatley',
      tel: '1-973-769-0247 x08896',
      address: '097 Kihn Skyway',
      opening_hours: '08:00',
      description: 'eum necessitatibus ea',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=68.67917708511362',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: 'Aubrey Zieme',
      tel: '(736) 562-0634 x81294',
      address: '642 Maiya Locks',
      opening_hours: '08:00',
      description: 'eos fugit corrupti',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=22.589822335431077',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
};

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
    fetchRestaurantsTop() {
      this.restaurants = dummyData.restaurants;
    },
    addFavorite(id) {
      this.restaurants = this.restaurants.map((restaurant) => {
        if (restaurant.id !== id) {
          return restaurant;
        }
        return {
          ...restaurant,
          isFavorited: true,
          FavoriteCount: restaurant.FavoriteCount + 1,
        };
      });
    },
    deleteFavorite(id) {
      this.restaurants = this.restaurants.map((restaurant) => {
        if (restaurant.id !== id) {
          return restaurant;
        }

        return {
          ...restaurant,
          isFavorited: false,
          FavoriteCount: restaurant.FavoriteCount - 1,
        };
      });
    },
  },
};
</script>
