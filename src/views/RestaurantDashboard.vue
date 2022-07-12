<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  restaurant: {
    id: 1,
    name: 'Sage Fritsch',
    tel: '873.005.5660',
    address: '562 Gleason Crest',
    opening_hours: '08:00',
    description: 'dolor expedita dolores',
    image:
      'https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472',
    viewCounts: 1,
    createdAt: '2022-07-05T22:26:19.000Z',
    updatedAt: '2022-07-07T19:36:29.000Z',
    CategoryId: 1,
    Category: {
      id: 1,
      name: '中式料理',
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    Comments: [
      {
        id: 1,
        text: 'Quisquam aut nemo voluptatum.',
        UserId: 1,
        RestaurantId: 1,
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
        User: {
          id: 1,
          name: 'root',
          email: 'root@example.com',
          password:
            '$2a$10$cogesrfZKY.OZ6b2da/bRuFDmBUcrpUPAtjiSKz8joA5lDnJF09oW',
          isAdmin: true,
          image: null,
          createdAt: '2022-07-05T22:26:19.000Z',
          updatedAt: '2022-07-05T22:26:19.000Z',
        },
      },
      {
        id: 51,
        text: 'Excepturi quam rerum ut molestiae corrupti cupiditate at dignissimos omnis.',
        UserId: 2,
        RestaurantId: 1,
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
        User: {
          id: 2,
          name: 'user1',
          email: 'user1@example.com',
          password:
            '$2a$10$.xp.DcsMhJvW7U2xT/DOmOXVMjSE.0LmAEqFQq8lviJqKuZJUANHu',
          isAdmin: false,
          image: null,
          createdAt: '2022-07-05T22:26:19.000Z',
          updatedAt: '2022-07-05T22:26:19.000Z',
        },
      },
      {
        id: 101,
        text: 'Reiciendis voluptatem id voluptatem.',
        UserId: 3,
        RestaurantId: 1,
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
        User: {
          id: 3,
          name: 'user2',
          email: 'user2@example.com',
          password:
            '$2a$10$cTp.NZ.DDAEpsYyK7AU2e.xknDEQvG38wrIVJ8KviketBvhTnj7Eq',
          isAdmin: false,
          image: null,
          createdAt: '2022-07-05T22:26:19.000Z',
          updatedAt: '2022-07-05T22:26:19.000Z',
        },
      },
    ],
  },
};

export default {
  name: 'RestaurantDashboard',
  data() {
    return {
      restaurant: {},
    };
  },
  created() {
    this.fetchRestaurant();
  },
  methods: {
    fetchRestaurant() {
      const {
        Category,
        Comments
      } = dummyData.restaurant

      this.restaurant = {
        ...dummyData.restaurant,
        categoryName: Category.name,
        commentsLength: Comments.length,
      };
    },
  },
};
</script>
