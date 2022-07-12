<template>
  <div class="container py-5">
    <!-- AdminNav Component -->
    <AdminNav />

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Email</th>
          <th scope="col">Role</th>
          <th scope="col" width="140">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.email }}</td>
          <td>{{ user.isAdmin ? 'admin' : 'user' }}</td>
          <td v-if="currentUser.id !== user.id">
            <button
              type="button"
              class="btn btn-link"
              @click.stop.prevent="toggleUserRole(user.id)"
            >
              {{ user.isAdmin ? 'set as user' : 'set as admin' }}
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
const dummyData = {
  users: [
    {
      id: 1,
      name: 'root',
      email: 'root@example.com',
      password: '$2a$10$cogesrfZKY.OZ6b2da/bRuFDmBUcrpUPAtjiSKz8joA5lDnJF09oW',
      isAdmin: true,
      image: null,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 2,
      name: 'user1',
      email: 'user1@example.com',
      password: '$2a$10$.xp.DcsMhJvW7U2xT/DOmOXVMjSE.0LmAEqFQq8lviJqKuZJUANHu',
      isAdmin: false,
      image: null,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
    {
      id: 3,
      name: 'user2',
      email: 'user2@example.com',
      password: '$2a$10$cTp.NZ.DDAEpsYyK7AU2e.xknDEQvG38wrIVJ8KviketBvhTnj7Eq',
      isAdmin: false,
      image: null,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
    },
  ],
};
const dummyUser = {
    "profile": {
        "id": 1,
        "name": "root",
        "email": "root@example.com",
        "password": "$2a$10$cogesrfZKY.OZ6b2da/bRuFDmBUcrpUPAtjiSKz8joA5lDnJF09oW",
        "isAdmin": true,
        "image": null,
        "createdAt": "2022-07-05T22:26:19.000Z",
        "updatedAt": "2022-07-05T22:26:19.000Z",
        "Comments": [
            {
                "id": 1,
                "text": "Quisquam aut nemo voluptatum.",
                "UserId": 1,
                "RestaurantId": 1,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 1,
                    "name": "Sage Fritsch",
                    "tel": "873.005.5660",
                    "address": "562 Gleason Crest",
                    "opening_hours": "08:00",
                    "description": "dolor expedita dolores",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.71546683155472",
                    "viewCounts": 1,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-07T19:36:29.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 5,
                "text": "Voluptatem eos dolorum odio commodi amet cum porro dolore nihil.",
                "UserId": 1,
                "RestaurantId": 5,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 12,
                "text": "Harum eos incidunt est recusandae.",
                "UserId": 1,
                "RestaurantId": 12,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 12,
                    "name": "Rod Marks",
                    "tel": "694-257-5173",
                    "address": "1145 Seth Center",
                    "opening_hours": "08:00",
                    "description": "Nihil qui eligendi atque. Impedit id et veritatis sed quas sed ipsum. Quia nesciunt id voluptas quod dolorem nesciunt. Dolorum vel ratione dolorem voluptates ratione quos molestiae.\n \rSunt expedita non quisquam quos eligendi fuga provident non vel. Sint voluptas quam ut iste sapiente ut. Et similique amet sint doloribus. Earum qui quia corporis nulla nisi vel eligendi quia. Iste omnis ratione repellendus dicta consequuntur. Reprehenderit iste vero quam nobis animi iusto.\n \rEt et nostrum quibusdam nobis eos tempore omnis. Blanditiis quo ex aut et. Debitis placeat ipsam ipsa magnam assumenda rerum. Voluptatum accusamus veritatis eius et. Quam qui eos ut et totam quia maxime labore.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.318466695748874",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 18,
                "text": "Assumenda nisi perspiciatis dolorem corrupti suscipit eos est numquam.",
                "UserId": 1,
                "RestaurantId": 18,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 18,
                    "name": "Maurice Bins",
                    "tel": "823-476-1246",
                    "address": "79221 Rice Well",
                    "opening_hours": "08:00",
                    "description": "et error culpa",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=18.918337457006885",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 23,
                "text": "Ullam quia aperiam reprehenderit sequi dolores doloribus qui ad.",
                "UserId": 1,
                "RestaurantId": 23,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 23,
                    "name": "Sylvia Flatley",
                    "tel": "1-266-021-8571 x335",
                    "address": "5646 August Overpass",
                    "opening_hours": "08:00",
                    "description": "Expedita eveniet beatae nemo et. Nemo molestiae voluptatum labore et impedit et quo. Itaque rem voluptatem.\n \rEt facilis est iste sequi eum ut. Cumque cumque voluptatem maiores aut illo quam quidem sapiente corrupti. Unde est provident libero aliquam ut aut voluptatem molestiae. Veniam ab hic dolor est officia qui.\n \rFacere ex corporis labore neque. Vel aut natus et suscipit ut. Deleniti accusamus et quasi non excepturi accusamus et reprehenderit numquam.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=58.62907323027764",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 25,
                "text": "Similique eum eum molestiae laboriosam quasi et voluptatem.",
                "UserId": 1,
                "RestaurantId": 25,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 25,
                    "name": "Jerald Wiza",
                    "tel": "(757) 973-7005 x0441",
                    "address": "756 Maria Street",
                    "opening_hours": "08:00",
                    "description": "Ex cumque ad ut odit vel blanditiis.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=9.364491008894383",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 29,
                "text": "Labore suscipit non saepe deleniti nisi.",
                "UserId": 1,
                "RestaurantId": 29,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 29,
                    "name": "Lewis Swaniawski",
                    "tel": "1-652-008-2943",
                    "address": "802 Yasmine Grove",
                    "opening_hours": "08:00",
                    "description": "et reiciendis illo",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=51.341076989561344",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 31,
                "text": "Aspernatur atque in a.",
                "UserId": 1,
                "RestaurantId": 31,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 31,
                    "name": "Rowena Bogisich",
                    "tel": "292.106.6450 x742",
                    "address": "57808 Alisha Branch",
                    "opening_hours": "08:00",
                    "description": "Debitis autem voluptatum commodi doloribus ipsam. Veritatis qui quo itaque. Nesciunt vero placeat porro ipsam.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=78.64037160654243",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 2
                }
            },
            {
                "id": 35,
                "text": "Quae explicabo autem rem quis ut neque atque.",
                "UserId": 1,
                "RestaurantId": 35,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 35,
                    "name": "Mr. Rafaela Schoen",
                    "tel": "(123) 912-9566",
                    "address": "9487 Julius Trafficway",
                    "opening_hours": "08:00",
                    "description": "magni",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=19.55913377509464",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 3
                }
            },
            {
                "id": 39,
                "text": "Quo minus sed qui at ut tempore.",
                "UserId": 1,
                "RestaurantId": 39,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 39,
                    "name": "Savanna O'Reilly",
                    "tel": "437-866-2118 x31454",
                    "address": "127 Nitzsche Crossing",
                    "opening_hours": "08:00",
                    "description": "nisi",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=42.18150863313805",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 42,
                "text": "Sed dolores blanditiis unde aut ut et iure.",
                "UserId": 1,
                "RestaurantId": 42,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 42,
                    "name": "Maiya Flatley",
                    "tel": "1-973-769-0247 x08896",
                    "address": "097 Kihn Skyway",
                    "opening_hours": "08:00",
                    "description": "eum necessitatibus ea",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.67917708511362",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 43,
                "text": "Mollitia sapiente quam sed eos.",
                "UserId": 1,
                "RestaurantId": 43,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 43,
                    "name": "Bernard Casper DDS",
                    "tel": "1-267-747-6873 x6348",
                    "address": "0268 Dickinson Falls",
                    "opening_hours": "08:00",
                    "description": "repudiandae",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.07205981616009",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 44,
                "text": "Accusantium dolor tempore eos.",
                "UserId": 1,
                "RestaurantId": 44,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 44,
                    "name": "Joy Lowe",
                    "tel": "1-248-034-2606 x975",
                    "address": "354 Dashawn Cove",
                    "opening_hours": "08:00",
                    "description": "Voluptate unde qui nulla. Quidem rerum quasi ratione ipsum. Beatae qui tempora delectus minus rem assumenda et.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=15.304819817476112",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 45,
                "text": "Corporis nostrum delectus et unde cumque unde veritatis.",
                "UserId": 1,
                "RestaurantId": 45,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 45,
                    "name": "Roselyn McLaughlin",
                    "tel": "(479) 706-9055 x91343",
                    "address": "82057 Ettie Throughway",
                    "opening_hours": "08:00",
                    "description": "Porro explicabo quae exercitationem sit laudantium rem voluptas in. Sit aut aut expedita modi commodi voluptate. Voluptatum aliquam iure ut.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.401057286026184",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 3
                }
            },
            {
                "id": 46,
                "text": "Inventore aut mollitia voluptate alias ipsum.",
                "UserId": 1,
                "RestaurantId": 46,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 46,
                    "name": "Kamren Brown",
                    "tel": "(467) 271-7341 x2849",
                    "address": "372 Doyle Orchard",
                    "opening_hours": "08:00",
                    "description": "Nobis cupiditate veritatis.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=81.22291896392373",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 50,
                "text": "Quis et occaecati laboriosam ut repudiandae ipsa illo quaerat non.",
                "UserId": 1,
                "RestaurantId": 50,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 50,
                    "name": "Mossie Bartoletti",
                    "tel": "(392) 036-9035",
                    "address": "805 Casper Harbor",
                    "opening_hours": "08:00",
                    "description": "Ut molestias excepturi magni et consequatur.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.563720368747315",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 55,
                "text": "Accusamus impedit rerum et aliquid est quos.",
                "UserId": 1,
                "RestaurantId": 5,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 57,
                "text": "Asperiores alias exercitationem.",
                "UserId": 1,
                "RestaurantId": 7,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 59,
                "text": "Laudantium ut sint hic itaque omnis et odio a vel.",
                "UserId": 1,
                "RestaurantId": 9,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 66,
                "text": "Cum nobis ut aut sunt voluptatibus suscipit quibusdam eveniet rerum.",
                "UserId": 1,
                "RestaurantId": 16,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 16,
                    "name": "Erika Barton",
                    "tel": "(836) 730-2100 x8041",
                    "address": "7836 Roel Knolls",
                    "opening_hours": "08:00",
                    "description": "Et facilis quia ipsa voluptatem autem consectetur expedita. Vel officia voluptatum quia est exercitationem dolore neque. Ab hic et natus minus. Voluptate ut voluptatem voluptatem ut. Et blanditiis culpa maiores eum voluptas expedita voluptas facilis. Quo nemo dolorem sint ut sunt odit.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=26.87862472687419",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 68,
                "text": "Deserunt sed quas perferendis doloremque sunt incidunt unde sed.",
                "UserId": 1,
                "RestaurantId": 18,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 18,
                    "name": "Maurice Bins",
                    "tel": "823-476-1246",
                    "address": "79221 Rice Well",
                    "opening_hours": "08:00",
                    "description": "et error culpa",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=18.918337457006885",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 74,
                "text": "Voluptates qui sint provident veniam qui voluptas quo.",
                "UserId": 1,
                "RestaurantId": 24,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 24,
                    "name": "Sam Bruen",
                    "tel": "(629) 463-2380 x76314",
                    "address": "6426 Taya Road",
                    "opening_hours": "08:00",
                    "description": "et",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=2.5644110751812166",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 2
                }
            },
            {
                "id": 82,
                "text": "Dolorem nesciunt natus quia mollitia rerum officiis et.",
                "UserId": 1,
                "RestaurantId": 32,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 32,
                    "name": "Abagail Paucek",
                    "tel": "014.032.0371",
                    "address": "611 Hulda Cliffs",
                    "opening_hours": "08:00",
                    "description": "Enim et distinctio est eius id et sit praesentium. Sed excepturi voluptatem quidem. In sed inventore tenetur.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=85.77944410896392",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 83,
                "text": "Dolorum molestias quaerat.",
                "UserId": 1,
                "RestaurantId": 33,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 33,
                    "name": "Rey Kling",
                    "tel": "1-545-345-0012 x5488",
                    "address": "689 Cummings Glens",
                    "opening_hours": "08:00",
                    "description": "dolor ducimus delectus",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=33.56804706189194",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 2
                }
            },
            {
                "id": 90,
                "text": "Neque veritatis neque aliquid quae eligendi omnis ut voluptas sapiente.",
                "UserId": 1,
                "RestaurantId": 40,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 40,
                    "name": "Aryanna Willms DVM",
                    "tel": "1-772-532-4095",
                    "address": "058 Botsford Street",
                    "opening_hours": "08:00",
                    "description": "et odit vel",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.482100741039826",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 91,
                "text": "Ea veniam sequi quibusdam porro repellat eum sed hic quae.",
                "UserId": 1,
                "RestaurantId": 41,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 41,
                    "name": "Aubrey Zieme",
                    "tel": "(736) 562-0634 x81294",
                    "address": "642 Maiya Locks",
                    "opening_hours": "08:00",
                    "description": "eos fugit corrupti",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=22.589822335431077",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 3
                }
            },
            {
                "id": 93,
                "text": "Eveniet illum inventore eius excepturi fugiat rem quae.",
                "UserId": 1,
                "RestaurantId": 43,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 43,
                    "name": "Bernard Casper DDS",
                    "tel": "1-267-747-6873 x6348",
                    "address": "0268 Dickinson Falls",
                    "opening_hours": "08:00",
                    "description": "repudiandae",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.07205981616009",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 95,
                "text": "Voluptatum natus ut aperiam corporis temporibus et est nobis ea.",
                "UserId": 1,
                "RestaurantId": 45,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 45,
                    "name": "Roselyn McLaughlin",
                    "tel": "(479) 706-9055 x91343",
                    "address": "82057 Ettie Throughway",
                    "opening_hours": "08:00",
                    "description": "Porro explicabo quae exercitationem sit laudantium rem voluptas in. Sit aut aut expedita modi commodi voluptate. Voluptatum aliquam iure ut.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.401057286026184",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 3
                }
            },
            {
                "id": 96,
                "text": "Aperiam ipsam non.",
                "UserId": 1,
                "RestaurantId": 46,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 46,
                    "name": "Kamren Brown",
                    "tel": "(467) 271-7341 x2849",
                    "address": "372 Doyle Orchard",
                    "opening_hours": "08:00",
                    "description": "Nobis cupiditate veritatis.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=81.22291896392373",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 104,
                "text": "Corrupti atque velit nemo repudiandae qui aspernatur nesciunt architecto.",
                "UserId": 1,
                "RestaurantId": 4,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 107,
                "text": "Ratione eos perspiciatis totam dolore aut ut est consectetur.",
                "UserId": 1,
                "RestaurantId": 7,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
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
                "id": 112,
                "text": "Voluptas ducimus aut aliquid consequatur ut sed.",
                "UserId": 1,
                "RestaurantId": 12,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 12,
                    "name": "Rod Marks",
                    "tel": "694-257-5173",
                    "address": "1145 Seth Center",
                    "opening_hours": "08:00",
                    "description": "Nihil qui eligendi atque. Impedit id et veritatis sed quas sed ipsum. Quia nesciunt id voluptas quod dolorem nesciunt. Dolorum vel ratione dolorem voluptates ratione quos molestiae.\n \rSunt expedita non quisquam quos eligendi fuga provident non vel. Sint voluptas quam ut iste sapiente ut. Et similique amet sint doloribus. Earum qui quia corporis nulla nisi vel eligendi quia. Iste omnis ratione repellendus dicta consequuntur. Reprehenderit iste vero quam nobis animi iusto.\n \rEt et nostrum quibusdam nobis eos tempore omnis. Blanditiis quo ex aut et. Debitis placeat ipsam ipsa magnam assumenda rerum. Voluptatum accusamus veritatis eius et. Quam qui eos ut et totam quia maxime labore.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.318466695748874",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 117,
                "text": "Rem itaque pariatur modi.",
                "UserId": 1,
                "RestaurantId": 17,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 17,
                    "name": "Percy Gutkowski",
                    "tel": "1-827-541-3037 x687",
                    "address": "2910 Cole Summit",
                    "opening_hours": "08:00",
                    "description": "id repellat voluptatem",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=98.37955769110019",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 119,
                "text": "Sed occaecati dolores vel earum sint officia itaque consequatur laboriosam.",
                "UserId": 1,
                "RestaurantId": 19,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 19,
                    "name": "Randi Rogahn",
                    "tel": "1-117-881-2540 x7839",
                    "address": "37591 Goyette Lodge",
                    "opening_hours": "08:00",
                    "description": "Quaerat odit provident.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=41.445127794954864",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 126,
                "text": "Aspernatur est minus et consequatur.",
                "UserId": 1,
                "RestaurantId": 26,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 26,
                    "name": "Waino Schmitt",
                    "tel": "(814) 647-5050 x2507",
                    "address": "30878 Stamm Trace",
                    "opening_hours": "08:00",
                    "description": "Et aut et in iure aspernatur nemo est ex similique.\nQuasi neque architecto est ut nostrum voluptatem tempora.\nVoluptas sunt repellendus dolores illo quae minus saepe voluptatibus dolore.\nVoluptatem asperiores animi quasi molestiae.\nSint rerum enim quia esse reiciendis in ipsa.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=20.60880358230537",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 129,
                "text": "Tempora ea pariatur molestias dolore consectetur voluptatibus consequatur.",
                "UserId": 1,
                "RestaurantId": 29,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 29,
                    "name": "Lewis Swaniawski",
                    "tel": "1-652-008-2943",
                    "address": "802 Yasmine Grove",
                    "opening_hours": "08:00",
                    "description": "et reiciendis illo",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=51.341076989561344",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 132,
                "text": "Qui labore est.",
                "UserId": 1,
                "RestaurantId": 32,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 32,
                    "name": "Abagail Paucek",
                    "tel": "014.032.0371",
                    "address": "611 Hulda Cliffs",
                    "opening_hours": "08:00",
                    "description": "Enim et distinctio est eius id et sit praesentium. Sed excepturi voluptatem quidem. In sed inventore tenetur.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=85.77944410896392",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 138,
                "text": "Amet occaecati quidem dolore facilis vel qui sint.",
                "UserId": 1,
                "RestaurantId": 38,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 38,
                    "name": "Stone Gleichner",
                    "tel": "494.602.4328 x79827",
                    "address": "3992 Afton Tunnel",
                    "opening_hours": "08:00",
                    "description": "minus sint explicabo",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=14.726231519977162",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 140,
                "text": "Voluptas omnis eos maiores numquam eius ullam ea.",
                "UserId": 1,
                "RestaurantId": 40,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 40,
                    "name": "Aryanna Willms DVM",
                    "tel": "1-772-532-4095",
                    "address": "058 Botsford Street",
                    "opening_hours": "08:00",
                    "description": "et odit vel",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=25.482100741039826",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            },
            {
                "id": 142,
                "text": "Ipsa nulla veritatis rerum libero est qui.",
                "UserId": 1,
                "RestaurantId": 42,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 42,
                    "name": "Maiya Flatley",
                    "tel": "1-973-769-0247 x08896",
                    "address": "097 Kihn Skyway",
                    "opening_hours": "08:00",
                    "description": "eum necessitatibus ea",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.67917708511362",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 143,
                "text": "Iste quaerat laboriosam nesciunt unde voluptatem accusantium deserunt.",
                "UserId": 1,
                "RestaurantId": 43,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 43,
                    "name": "Bernard Casper DDS",
                    "tel": "1-267-747-6873 x6348",
                    "address": "0268 Dickinson Falls",
                    "opening_hours": "08:00",
                    "description": "repudiandae",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.07205981616009",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 4
                }
            },
            {
                "id": 146,
                "text": "Voluptate esse id.",
                "UserId": 1,
                "RestaurantId": 46,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 46,
                    "name": "Kamren Brown",
                    "tel": "(467) 271-7341 x2849",
                    "address": "372 Doyle Orchard",
                    "opening_hours": "08:00",
                    "description": "Nobis cupiditate veritatis.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=81.22291896392373",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 1
                }
            },
            {
                "id": 149,
                "text": "Quibusdam qui est quis sapiente.",
                "UserId": 1,
                "RestaurantId": 49,
                "createdAt": "2022-07-05T22:26:19.000Z",
                "updatedAt": "2022-07-05T22:26:19.000Z",
                "Restaurant": {
                    "id": 49,
                    "name": "Nikolas Schuster",
                    "tel": "060.512.5232 x374",
                    "address": "9835 Royal Camp",
                    "opening_hours": "08:00",
                    "description": "Et sit eius aut quo expedita. Fugiat expedita voluptas at enim odit perferendis. Repudiandae est laborum debitis earum consequatur ad quam.\n \rPorro qui et nemo. Natus repellat placeat fuga et qui mollitia corporis id fugit. Delectus sit doloremque. Id nihil assumenda eos necessitatibus perferendis corporis voluptatum et.\n \rEsse ut odit voluptate explicabo ex. Et architecto rem et quidem dolor consequatur earum delectus. A recusandae dolorum minima. Dolorem quia expedita sit vitae. Dolor omnis voluptatem non deleniti ipsum accusantium optio recusandae.",
                    "image": "https://loremflickr.com/320/240/restaurant,food/?random=32.81392081379772",
                    "viewCounts": 0,
                    "createdAt": "2022-07-05T22:26:19.000Z",
                    "updatedAt": "2022-07-05T22:26:19.000Z",
                    "CategoryId": 5
                }
            }
        ],
        "FavoritedRestaurants": [],
        "Followers": [],
        "Followings": []
    },
    "isFollowed": false
}
import AdminNav from '@/components/AdminNav';

export default {
  name: 'AdminUsers',
  components: {
    AdminNav,
  },
  data() {
    return {
      users: [],
      currentUser: {}
    };
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users;
      this.currentUser = dummyUser.profile
    },
    toggleUserRole(userId) {
      this.users = this.users.map((user) => {
        if (user.id === userId) {
          return {
            ...user,
            isAdmin: !user.isAdmin,
          };
        }

        return user;
      });
    },
  },
};
</script>
