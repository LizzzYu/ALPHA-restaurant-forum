<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="categoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue';
import RestaurantCard from '../components/RestaurantCard.vue';
import RestaurantsNavPills from '../components/RestaurantsNavPills.vue';
import RestaurantsPagination from '../components/RestaurantsPagination.vue';

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: 'Sage Fritsch',
      tel: '873.005.5660',
      address: '562 Gleason Crest',
      opening_hours: '08:00',
      description: 'dolor expedita dolores',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: 'Michale Terry',
      tel: '191-306-4188',
      address: '9717 Camden Stravenue',
      opening_hours: '08:00',
      description: 'magnam',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=21.984062753839506',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: 'Pablo Jakubowski',
      tel: '1-459-022-4857 x617',
      address: '8346 Jerde Stravenue',
      opening_hours: '08:00',
      description: 'Eligendi rerum eius vel et.\nSed sed natus asperior',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=33.963030808814686',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 4,
      Category: {
        id: 4,
        name: '墨西哥料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: 'Herbert Nolan',
      tel: '1-870-268-6266 x8017',
      address: '42462 Eloisa Lodge',
      opening_hours: '08:00',
      description: 'Maxime quod qui. Magni vel mollitia sequi officia ',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=65.89130615192533',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: 'Barney Frami',
      tel: '(937) 011-5684',
      address: '9591 Mosciski Overpass',
      opening_hours: '08:00',
      description: 'est',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=69.76878364379924',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: 'Stan Robel',
      tel: '693-826-5435 x281',
      address: '3630 Torp Cape',
      opening_hours: '08:00',
      description: 'Quas sint aperiam consequatur ut maiores.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.892248381258621',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      Category: {
        id: 3,
        name: '義大利料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: 'Donny Ernser',
      tel: '928.657.7071',
      address: '8223 Gulgowski Mountain',
      opening_hours: '08:00',
      description: 'velit',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=70.29289129877058',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      Category: {
        id: 3,
        name: '義大利料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: 'Manuel Morar',
      tel: '1-669-656-7052 x3296',
      address: '4990 Kassulke Isle',
      opening_hours: '08:00',
      description: 'ullam aperiam ratione',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=66.73896799644108',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      Category: {
        id: 3,
        name: '義大利料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Irving O'Connell",
      tel: '576.197.3207 x767',
      address: '047 Jarret Ridges',
      opening_hours: '08:00',
      description: 'doloremque',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=5.535457515693554',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: 'Kellie Mann',
      tel: '(628) 978-0296 x76616',
      address: '67975 Price Locks',
      opening_hours: '08:00',
      description: 'Id at placeat odio accusantium necessitatibus sed ',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=88.33063931695362',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 3,
      Category: {
        id: 3,
        name: '義大利料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: '中式料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 2,
      name: '日本料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 3,
      name: '義大利料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 4,
      name: '墨西哥料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 5,
      name: '素食料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 6,
      name: '美式料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 7,
      name: '複合式料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
  ],
  categoryId: '',
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1,
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;

      (this.restaurants = restaurants),
        (this.categories = categories),
        (this.categoryId = categoryId),
        (this.currentPage = page),
        (this.totalPage = totalPage),
        (this.previousPage = prev),
        (this.nextPage = next);
    },
  },
};
</script>
