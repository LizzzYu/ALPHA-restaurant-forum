<template>
  <div class="container py-5">
    <NavTabs />

    <h1 class="mt-5">
      最新動態
    </h1>
    <hr>
    <div class="row">
      <div class="col-md-6">
        <h3>最新餐廳</h3>
        <!-- 最新評論 NewestComments-->
        <NewestRestaurants
          :restaurants=restaurants />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments
          :comments=comments />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import NewestRestaurants from '../components/NewestRestaurants.vue'
import NewestComments from '../components/NewestComments.vue'

const dummyData = {
    "restaurants": [
        {
            "id": 1,
            "name": "Sage Fritsch",
            "tel": "873.005.5660",
            "address": "562 Gleason Crest",
            "opening_hours": "08:00",
            "description": "dolor expedita dolores",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 1,
            "Category": {
                "id": 1,
                "name": "中式料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 2,
            "name": "Michale Terry",
            "tel": "191-306-4188",
            "address": "9717 Camden Stravenue",
            "opening_hours": "08:00",
            "description": "magnam",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.984062753839506",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 3,
            "name": "Pablo Jakubowski",
            "tel": "1-459-022-4857 x617",
            "address": "8346 Jerde Stravenue",
            "opening_hours": "08:00",
            "description": "Eligendi rerum eius vel et.\nSed sed natus asperiores maxime repellendus fugiat neque molestiae et.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=33.963030808814686",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 4,
            "Category": {
                "id": 4,
                "name": "墨西哥料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 4,
            "name": "Herbert Nolan",
            "tel": "1-870-268-6266 x8017",
            "address": "42462 Eloisa Lodge",
            "opening_hours": "08:00",
            "description": "Maxime quod qui. Magni vel mollitia sequi officia maxime dicta dolorem. Voluptatem pariatur occaecati ut in nisi reprehenderit natus ex blanditiis. Et aliquid praesentium et. Officia ducimus molestias fugiat.\n \rAut natus quia soluta sunt. Molestiae et et laborum est voluptates laboriosam esse temporibus. Inventore iste et aliquid illum.\n \rQuidem expedita quibusdam. Quaerat sint quam ipsum perspiciatis voluptas. Laborum tenetur quae aliquam. Amet aut aut impedit ab veritatis reiciendis adipisci.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=65.89130615192533",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 5,
            "name": "Barney Frami",
            "tel": "(937) 011-5684",
            "address": "9591 Mosciski Overpass",
            "opening_hours": "08:00",
            "description": "est",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=69.76878364379924",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 6,
            "name": "Stan Robel",
            "tel": "693-826-5435 x281",
            "address": "3630 Torp Cape",
            "opening_hours": "08:00",
            "description": "Quas sint aperiam consequatur ut maiores.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=15.892248381258621",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 7,
            "name": "Donny Ernser",
            "tel": "928.657.7071",
            "address": "8223 Gulgowski Mountain",
            "opening_hours": "08:00",
            "description": "velit",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=70.29289129877058",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 8,
            "name": "Manuel Morar",
            "tel": "1-669-656-7052 x3296",
            "address": "4990 Kassulke Isle",
            "opening_hours": "08:00",
            "description": "ullam aperiam ratione",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=66.73896799644108",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 9,
            "name": "Irving O'Connell",
            "tel": "576.197.3207 x767",
            "address": "047 Jarret Ridges",
            "opening_hours": "08:00",
            "description": "doloremque",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=5.535457515693554",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 5,
            "Category": {
                "id": 5,
                "name": "素食料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        },
        {
            "id": 10,
            "name": "Kellie Mann",
            "tel": "(628) 978-0296 x76616",
            "address": "67975 Price Locks",
            "opening_hours": "08:00",
            "description": "Id at placeat odio accusantium necessitatibus sed dignissimos. Molestiae nam omnis aut sed cupiditate sunt repellendus necessitatibus. Aliquid amet quia. Commodi voluptates quasi ab eos enim doloremque accusantium illum tempore. Veritatis magni ipsum repudiandae harum voluptates exercitationem.",
            "image": "https://loremflickr.com/320/240/restaurant,food/?random=88.33063931695362",
            "viewCounts": 0,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "CategoryId": 3,
            "Category": {
                "id": 3,
                "name": "義大利料理",
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z"
            }
        }
    ],
    "comments": [
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
            },
            "Restaurant": {
                "id": 1,
                "name": "Sage Fritsch",
                "tel": "873.005.5660",
                "address": "562 Gleason Crest",
                "opening_hours": "08:00",
                "description": "dolor expedita dolores",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 1
            }
        },
        {
            "id": 2,
            "text": "Unde error eum ullam odio qui.",
            "UserId": 3,
            "RestaurantId": 2,
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
            },
            "Restaurant": {
                "id": 2,
                "name": "Michale Terry",
                "tel": "191-306-4188",
                "address": "9717 Camden Stravenue",
                "opening_hours": "08:00",
                "description": "magnam",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=21.984062753839506",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 3,
            "text": "Velit accusantium et sed ipsam itaque dignissimos et doloremque.",
            "UserId": 2,
            "RestaurantId": 3,
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
            },
            "Restaurant": {
                "id": 3,
                "name": "Pablo Jakubowski",
                "tel": "1-459-022-4857 x617",
                "address": "8346 Jerde Stravenue",
                "opening_hours": "08:00",
                "description": "Eligendi rerum eius vel et.\nSed sed natus asperiores maxime repellendus fugiat neque molestiae et.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=33.963030808814686",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 4
            }
        },
        {
            "id": 4,
            "text": "Rerum quidem fugiat voluptatem rerum quibusdam expedita.",
            "UserId": 2,
            "RestaurantId": 4,
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
            },
            "Restaurant": {
                "id": 4,
                "name": "Herbert Nolan",
                "tel": "1-870-268-6266 x8017",
                "address": "42462 Eloisa Lodge",
                "opening_hours": "08:00",
                "description": "Maxime quod qui. Magni vel mollitia sequi officia maxime dicta dolorem. Voluptatem pariatur occaecati ut in nisi reprehenderit natus ex blanditiis. Et aliquid praesentium et. Officia ducimus molestias fugiat.\n \rAut natus quia soluta sunt. Molestiae et et laborum est voluptates laboriosam esse temporibus. Inventore iste et aliquid illum.\n \rQuidem expedita quibusdam. Quaerat sint quam ipsum perspiciatis voluptas. Laborum tenetur quae aliquam. Amet aut aut impedit ab veritatis reiciendis adipisci.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=65.89130615192533",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 5,
            "text": "Voluptatem eos dolorum odio commodi amet cum porro dolore nihil.",
            "UserId": 1,
            "RestaurantId": 5,
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
            },
            "Restaurant": {
                "id": 5,
                "name": "Barney Frami",
                "tel": "(937) 011-5684",
                "address": "9591 Mosciski Overpass",
                "opening_hours": "08:00",
                "description": "est",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=69.76878364379924",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 6,
            "text": "Optio ducimus delectus ipsum facilis.",
            "UserId": 3,
            "RestaurantId": 6,
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
            },
            "Restaurant": {
                "id": 6,
                "name": "Stan Robel",
                "tel": "693-826-5435 x281",
                "address": "3630 Torp Cape",
                "opening_hours": "08:00",
                "description": "Quas sint aperiam consequatur ut maiores.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=15.892248381258621",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 3
            }
        },
        {
            "id": 7,
            "text": "Quia quia deserunt maiores repellat ut ex.",
            "UserId": 3,
            "RestaurantId": 7,
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
            },
            "Restaurant": {
                "id": 7,
                "name": "Donny Ernser",
                "tel": "928.657.7071",
                "address": "8223 Gulgowski Mountain",
                "opening_hours": "08:00",
                "description": "velit",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=70.29289129877058",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 3
            }
        },
        {
            "id": 8,
            "text": "Nobis sed iure non et.",
            "UserId": 2,
            "RestaurantId": 8,
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
            },
            "Restaurant": {
                "id": 8,
                "name": "Manuel Morar",
                "tel": "1-669-656-7052 x3296",
                "address": "4990 Kassulke Isle",
                "opening_hours": "08:00",
                "description": "ullam aperiam ratione",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=66.73896799644108",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 3
            }
        },
        {
            "id": 9,
            "text": "Excepturi unde labore eos voluptatem dolorem quia.",
            "UserId": 2,
            "RestaurantId": 9,
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
            },
            "Restaurant": {
                "id": 9,
                "name": "Irving O'Connell",
                "tel": "576.197.3207 x767",
                "address": "047 Jarret Ridges",
                "opening_hours": "08:00",
                "description": "doloremque",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=5.535457515693554",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 5
            }
        },
        {
            "id": 10,
            "text": "Quaerat ex deserunt atque.",
            "UserId": 2,
            "RestaurantId": 10,
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
            },
            "Restaurant": {
                "id": 10,
                "name": "Kellie Mann",
                "tel": "(628) 978-0296 x76616",
                "address": "67975 Price Locks",
                "opening_hours": "08:00",
                "description": "Id at placeat odio accusantium necessitatibus sed dignissimos. Molestiae nam omnis aut sed cupiditate sunt repellendus necessitatibus. Aliquid amet quia. Commodi voluptates quasi ab eos enim doloremque accusantium illum tempore. Veritatis magni ipsum repudiandae harum voluptates exercitationem.",
                "image": "https://loremflickr.com/320/240/restaurant,food/?random=88.33063931695362",
                "viewCounts": 0,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "CategoryId": 3
            }
        }
    ]
}

export default {
  name: 'RestaurantFeeds',
  components: {
    NavTabs,
    NewestRestaurants,
    NewestComments
  },
  data() {
    return {
      restaurants: [],
      comments: [],
    }
  },
  created() {
    this.fetchFeeds()
  },
  methods: {
    fetchFeeds() {
      this.restaurants = dummyData.restaurants
      this.comments = dummyData.comments
    },
  }
}
</script>