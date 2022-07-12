<template>
  <div class="container py-5">
    <h1>餐廳描述頁</h1>
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail
      :initial-restaurant=restaurant />
    <hr>
    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment" />
    <!-- 新增評論 CreateComment -->
    <CreateComment
      :restaurant-id="restaurant.id"
      @after-create-comment="afterCreateComment" />
  </div>
</template>

<script>
import RestaurantDetail from '../components/RestaurantDetail.vue'
import RestaurantComments from '../components/RestaurantComments.vue'
import CreateComment from '../components/CreateComment.vue'

const dummyData = {
    "restaurant": {
        "id": 1,
        "name": "Sage Fritsch",
        "tel": "873.005.5660",
        "address": "562 Gleason Crest",
        "opening_hours": "08:00",
        "description": "dolor expedita dolores",
        "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472",
        "viewCounts": 1,
        "createdAt": "2022-07-05T22:26:19.000Z",
        "updatedAt": "2022-07-07T19:36:29.400Z",
        "CategoryId": 1,
        "Category": {
            "id": 1,
            "name": "中式料理",
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z"
        },
        "FavoritedUsers": [],
        "LikedUsers": [],
        "Comments": [
            {
                "id": 101,
                "text": "Reiciendis voluptatem id voluptatem.",
                "UserId": 3,
                "RestaurantId": 1,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "User": {
                    "id": 3,
                    "name": "user2",
                    "email": "user2@example.com",
                    "password": "$2a$10$cTp.NZ.DDAEpsYyK7AU2e.xknDEQvG38wrIVJ8KviketBvhTnj7Eq",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z"
                }
            },
            {
                "id": 51,
                "text": "Excepturi quam rerum ut molestiae corrupti cupiditate at dignissimos omnis.",
                "UserId": 2,
                "RestaurantId": 1,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "User": {
                    "id": 2,
                    "name": "user1",
                    "email": "user1@example.com",
                    "password": "$2a$10$.xp.DcsMhJvW7U2xT/DOmOXVMjSE.0LmAEqFQq8lviJqKuZJUANHu",
                    "isAdmin": false,
                    "image": null,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z"
                }
            },
            {
                "id": 1,
                "text": "Quisquam aut nemo voluptatum.",
                "UserId": 1,
                "RestaurantId": 1,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "User": {
                    "id": 1,
                    "name": "root",
                    "email": "root@example.com",
                    "password": "$2a$10$cogesrfZKY.OZ6b2da/bRuFDmBUcrpUPAtjiSKz8joA5lDnJF09oW",
                    "isAdmin": true,
                    "image": null,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z"
                }
            }
        ]
    },
    "isFavorited": false,
    "isLiked": false
}

const dummyUser = {
  currentUser: {
    id: 1,
    name: '管理者',
    email: 'root@example.com',
    image: 'https://i.pravatar.cc/300',
    isAdmin: true
  },
  isAuthenticated: true
}

export default {
  name: 'Restaurant',
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment
  },
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        image: '',
        openingHours: '',
        tel: '',
        address: '',
        description: '',
        isFavorited: false,
        isLiked: false
      },
      restaurantComments: [],
      currentUser: dummyUser.currentUser
    }
  },
  created() {
    const { id: restaurantId } = this.$route.params;
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant(restaurantId) {
      console.log('fetchRestaurant id: ', restaurantId)
      this.restaurant = {
        id: dummyData.restaurant.id,
        name: dummyData.restaurant.name,
        categoryName: dummyData.restaurant.Category.name,
        image: dummyData.restaurant.image,
        openingHours: dummyData.restaurant.opening_hours,
        tel: dummyData.restaurant.tel,
        address: dummyData.restaurant.address,
        description: dummyData.restaurant.description,
        isFavorited: dummyData.isFavorited,
        isLiked: dummyData.isLiked,
      }

      this.restaurantComments = dummyData.restaurant.Comments
    },
    afterDeleteComment(commentId) {
      this.restaurantComments = this.restaurantComments.filter(
        comment => comment.id !== commentId
      )
    },
    afterCreateComment(payload) {
      const { commentId, restaurantId, text } = payload
      this.restaurantComments.push({
        id: commentId,
        RestaurantId: restaurantId,
        User: {
          id: this.currentUser.id,
          name: this.currentUser.name
        },
        text,
        createdAt: new Date()
      })
    },
  }
}
</script>