<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Category</th>
        <th scope="col">Name</th>
        <th scope="col" width="300">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="restaurant in restaurants" :key="restaurant.id">
        <th scope="row">
          {{ restaurant.id }}
        </th>
        <td>{{ restaurant.Category ? restaurant.Category.name : '未分類' }}</td>
        <td>{{ restaurant.name }}</td>
        <td class="d-flex justify-content-between">
          <router-link
            :to="{ name: 'admin-restaurant', params: { id: restaurant.id } }"
            class="btn btn-link"
          >
            Show
          </router-link>

          <router-link
            :to="{
              name: 'admin-restaurant-edit',
              params: { id: restaurant.id },
            }"
            class="btn btn-link"
            >Edit</router-link
          >

          <button
            @click.stop.prevent="deleteRestaurant(restaurant.id)"
            type="button"
            class="btn btn-link"
          >
            Delete
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
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
    },
    {
      id: 3,
      name: 'Pablo Jakubowski',
      tel: '1-459-022-4857 x617',
      address: '8346 Jerde Stravenue',
      opening_hours: '08:00',
      description:
        'Eligendi rerum eius vel et.\nSed sed natus asperiores maxime repellendus fugiat neque molestiae et.',
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
    },
    {
      id: 4,
      name: 'Herbert Nolan',
      tel: '1-870-268-6266 x8017',
      address: '42462 Eloisa Lodge',
      opening_hours: '08:00',
      description:
        'Maxime quod qui. Magni vel mollitia sequi officia maxime dicta dolorem. Voluptatem pariatur occaecati ut in nisi reprehenderit natus ex blanditiis. Et aliquid praesentium et. Officia ducimus molestias fugiat.\n \rAut natus quia soluta sunt. Molestiae et et laborum est voluptates laboriosam esse temporibus. Inventore iste et aliquid illum.\n \rQuidem expedita quibusdam. Quaerat sint quam ipsum perspiciatis voluptas. Laborum tenetur quae aliquam. Amet aut aut impedit ab veritatis reiciendis adipisci.',
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
    },
    {
      id: 10,
      name: 'Kellie Mann',
      tel: '(628) 978-0296 x76616',
      address: '67975 Price Locks',
      opening_hours: '08:00',
      description:
        'Id at placeat odio accusantium necessitatibus sed dignissimos. Molestiae nam omnis aut sed cupiditate sunt repellendus necessitatibus. Aliquid amet quia. Commodi voluptates quasi ab eos enim doloremque accusantium illum tempore. Veritatis magni ipsum repudiandae harum voluptates exercitationem.',
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
    },
    {
      id: 11,
      name: 'Darlene Monahan',
      tel: '294.848.7945 x02833',
      address: '37482 Schuster Rapid',
      opening_hours: '08:00',
      description:
        'Sit et eos odio ab ducimus velit. Corporis illum debitis qui recusandae nisi omnis soluta omnis amet. Dolorum sint nulla animi optio tenetur sed. Expedita distinctio rerum. Libero accusamus dolorem vitae. Animi nihil sunt et animi ut atque.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=42.685543155354864',
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
    },
    {
      id: 12,
      name: 'Rod Marks',
      tel: '694-257-5173',
      address: '1145 Seth Center',
      opening_hours: '08:00',
      description:
        'Nihil qui eligendi atque. Impedit id et veritatis sed quas sed ipsum. Quia nesciunt id voluptas quod dolorem nesciunt. Dolorum vel ratione dolorem voluptates ratione quos molestiae.\n \rSunt expedita non quisquam quos eligendi fuga provident non vel. Sint voluptas quam ut iste sapiente ut. Et similique amet sint doloribus. Earum qui quia corporis nulla nisi vel eligendi quia. Iste omnis ratione repellendus dicta consequuntur. Reprehenderit iste vero quam nobis animi iusto.\n \rEt et nostrum quibusdam nobis eos tempore omnis. Blanditiis quo ex aut et. Debitis placeat ipsam ipsa magnam assumenda rerum. Voluptatum accusamus veritatis eius et. Quam qui eos ut et totam quia maxime labore.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=38.318466695748874',
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
    },
    {
      id: 13,
      name: 'Kayden Langworth',
      tel: '396.100.7391 x25365',
      address: '9969 Emmie Gateway',
      opening_hours: '08:00',
      description:
        'At voluptatem ipsam ipsum dolor sed deserunt. Sint eos quia repudiandae reprehenderit expedita amet accusamus maxime magni. Velit voluptatibus exercitationem. Ea et quibusdam eos officia est et quo.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=52.57502688668363',
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
    },
    {
      id: 14,
      name: 'Austen Kozey',
      tel: '(284) 076-3494',
      address: '2276 Windler Fort',
      opening_hours: '08:00',
      description: 'consequatur',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=84.90662742628443',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 15,
      name: 'Trudie Connelly',
      tel: '(973) 098-4178',
      address: '0228 Rosenbaum Pass',
      opening_hours: '08:00',
      description:
        'Nesciunt autem reprehenderit tempora nostrum sit est tenetur quos.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=38.10424277125002',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 16,
      name: 'Erika Barton',
      tel: '(836) 730-2100 x8041',
      address: '7836 Roel Knolls',
      opening_hours: '08:00',
      description:
        'Et facilis quia ipsa voluptatem autem consectetur expedita. Vel officia voluptatum quia est exercitationem dolore neque. Ab hic et natus minus. Voluptate ut voluptatem voluptatem ut. Et blanditiis culpa maiores eum voluptas expedita voluptas facilis. Quo nemo dolorem sint ut sunt odit.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=26.87862472687419',
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
    },
    {
      id: 17,
      name: 'Percy Gutkowski',
      tel: '1-827-541-3037 x687',
      address: '2910 Cole Summit',
      opening_hours: '08:00',
      description: 'id repellat voluptatem',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=98.37955769110019',
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
    },
    {
      id: 18,
      name: 'Maurice Bins',
      tel: '823-476-1246',
      address: '79221 Rice Well',
      opening_hours: '08:00',
      description: 'et error culpa',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=18.918337457006885',
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
    },
    {
      id: 19,
      name: 'Randi Rogahn',
      tel: '1-117-881-2540 x7839',
      address: '37591 Goyette Lodge',
      opening_hours: '08:00',
      description: 'Quaerat odit provident.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=41.445127794954864',
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
    },
    {
      id: 20,
      name: 'Eugene Gibson',
      tel: '1-443-810-3033 x50443',
      address: '994 Abbigail Keys',
      opening_hours: '08:00',
      description: 'tempora',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=30.258214367292503',
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
    },
    {
      id: 21,
      name: 'Major Kassulke',
      tel: '1-424-266-3933',
      address: '9031 Bartell Mountains',
      opening_hours: '08:00',
      description: 'Ex et necessitatibus asperiores voluptatum laborum.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=62.25290255754581',
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
    },
    {
      id: 22,
      name: 'Katlyn Labadie',
      tel: '1-413-067-4605 x038',
      address: '25634 Missouri Junctions',
      opening_hours: '08:00',
      description:
        'Tempora est repudiandae omnis nam sed voluptatibus. Voluptatem molestiae iusto qui molestiae sed. Aut voluptatem provident dolorem et. Eos natus non dolor quis. Et ut amet dolor porro accusamus nemo ut. Laborum saepe possimus sit velit consequatur accusantium rerum id occaecati.\n \rEst minima et et quia laudantium et nemo qui et. Exercitationem soluta iste quas aliquid. Cumque labore et sit aut alias quos sunt deleniti. Praesentium quam earum inventore error. Fuga fugit iure blanditiis.\n \rSit est et. Neque ab modi inventore atque atque aut. Consequatur veniam eum aliquid. Enim officiis autem impedit.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=98.47335747141616',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 23,
      name: 'Sylvia Flatley',
      tel: '1-266-021-8571 x335',
      address: '5646 August Overpass',
      opening_hours: '08:00',
      description:
        'Expedita eveniet beatae nemo et. Nemo molestiae voluptatum labore et impedit et quo. Itaque rem voluptatem.\n \rEt facilis est iste sequi eum ut. Cumque cumque voluptatem maiores aut illo quam quidem sapiente corrupti. Unde est provident libero aliquam ut aut voluptatem molestiae. Veniam ab hic dolor est officia qui.\n \rFacere ex corporis labore neque. Vel aut natus et suscipit ut. Deleniti accusamus et quasi non excepturi accusamus et reprehenderit numquam.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=58.62907323027764',
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
    },
    {
      id: 24,
      name: 'Sam Bruen',
      tel: '(629) 463-2380 x76314',
      address: '6426 Taya Road',
      opening_hours: '08:00',
      description: 'et',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=2.5644110751812166',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 25,
      name: 'Jerald Wiza',
      tel: '(757) 973-7005 x0441',
      address: '756 Maria Street',
      opening_hours: '08:00',
      description: 'Ex cumque ad ut odit vel blanditiis.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.364491008894383',
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
    },
    {
      id: 26,
      name: 'Waino Schmitt',
      tel: '(814) 647-5050 x2507',
      address: '30878 Stamm Trace',
      opening_hours: '08:00',
      description:
        'Et aut et in iure aspernatur nemo est ex similique.\nQuasi neque architecto est ut nostrum voluptatem tempora.\nVoluptas sunt repellendus dolores illo quae minus saepe voluptatibus dolore.\nVoluptatem asperiores animi quasi molestiae.\nSint rerum enim quia esse reiciendis in ipsa.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=20.60880358230537',
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
    },
    {
      id: 27,
      name: 'Lonie Dach V',
      tel: '1-262-152-5704 x907',
      address: '49005 Delia Mountain',
      opening_hours: '08:00',
      description: 'Deserunt eos molestiae ut quam ut et.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=89.41730786483619',
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
    },
    {
      id: 28,
      name: 'Lukas Hirthe',
      tel: '938.436.3225',
      address: '6164 Arnulfo Green',
      opening_hours: '08:00',
      description:
        'Id aut ipsam mollitia id.\nInventore ut velit id iusto.\nRecusandae ipsam dolorum dolore pariatur culpa iure eum minus sapiente.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=3.5891201524586025',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 29,
      name: 'Lewis Swaniawski',
      tel: '1-652-008-2943',
      address: '802 Yasmine Grove',
      opening_hours: '08:00',
      description: 'et reiciendis illo',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=51.341076989561344',
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
    },
    {
      id: 30,
      name: 'Cody Wyman',
      tel: '(626) 383-9667',
      address: '878 Rippin Route',
      opening_hours: '08:00',
      description:
        'Fugiat qui ducimus eos sapiente eum qui libero laboriosam ipsa. Nam ut natus culpa atque dolorem dignissimos odit. Qui quaerat sint aperiam ex eligendi autem eaque voluptas quod. Magni minus iure earum ad aut. Vitae inventore sapiente debitis occaecati sint.\n \rEst repellat iste. Assumenda quaerat recusandae voluptatibus impedit quibusdam. Quis rerum laborum perferendis adipisci.\n \rSit voluptas sint quia. Accusamus facilis sed fugiat provident ipsum harum. Doloribus consectetur harum excepturi iusto fugiat. Vel aut sed consequatur et asperiores quisquam at. Occaecati unde soluta magnam eveniet.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=1.5322282135811216',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 31,
      name: 'Rowena Bogisich',
      tel: '292.106.6450 x742',
      address: '57808 Alisha Branch',
      opening_hours: '08:00',
      description:
        'Debitis autem voluptatum commodi doloribus ipsam. Veritatis qui quo itaque. Nesciunt vero placeat porro ipsam.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=78.64037160654243',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 32,
      name: 'Abagail Paucek',
      tel: '014.032.0371',
      address: '611 Hulda Cliffs',
      opening_hours: '08:00',
      description:
        'Enim et distinctio est eius id et sit praesentium. Sed excepturi voluptatem quidem. In sed inventore tenetur.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=85.77944410896392',
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
    },
    {
      id: 33,
      name: 'Rey Kling',
      tel: '1-545-345-0012 x5488',
      address: '689 Cummings Glens',
      opening_hours: '08:00',
      description: 'dolor ducimus delectus',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=33.56804706189194',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 34,
      name: 'Alexandrine Muller',
      tel: '853-231-8985 x70361',
      address: '2534 Savanah Cove',
      opening_hours: '08:00',
      description:
        'Quis veniam consequuntur ut deserunt doloribus et veniam libero.\nCupiditate dolor quis fugit cum ut sunt.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=39.410464964217205',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 35,
      name: 'Mr. Rafaela Schoen',
      tel: '(123) 912-9566',
      address: '9487 Julius Trafficway',
      opening_hours: '08:00',
      description: 'magni',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=19.55913377509464',
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
    },
    {
      id: 36,
      name: 'May Lind Sr.',
      tel: '1-869-105-7221 x690',
      address: '294 Sam Ridges',
      opening_hours: '08:00',
      description: 'in enim omnis',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=94.47943769275338',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 37,
      name: 'Rozella Mitchell',
      tel: '667-517-4080 x50650',
      address: '5995 Dorcas Crescent',
      opening_hours: '08:00',
      description: 'maxime iure molestias',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=50.02831557769034',
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
    },
    {
      id: 38,
      name: 'Stone Gleichner',
      tel: '494.602.4328 x79827',
      address: '3992 Afton Tunnel',
      opening_hours: '08:00',
      description: 'minus sint explicabo',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=14.726231519977162',
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
    },
    {
      id: 39,
      name: "Savanna O'Reilly",
      tel: '437-866-2118 x31454',
      address: '127 Nitzsche Crossing',
      opening_hours: '08:00',
      description: 'nisi',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=42.18150863313805',
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
    },
    {
      id: 40,
      name: 'Aryanna Willms DVM',
      tel: '1-772-532-4095',
      address: '058 Botsford Street',
      opening_hours: '08:00',
      description: 'et odit vel',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=25.482100741039826',
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
      Category: {
        id: 3,
        name: '義大利料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
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
      Category: {
        id: 4,
        name: '墨西哥料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
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
      Category: {
        id: 4,
        name: '墨西哥料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 44,
      name: 'Joy Lowe',
      tel: '1-248-034-2606 x975',
      address: '354 Dashawn Cove',
      opening_hours: '08:00',
      description:
        'Voluptate unde qui nulla. Quidem rerum quasi ratione ipsum. Beatae qui tempora delectus minus rem assumenda et.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.304819817476112',
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
    },
    {
      id: 45,
      name: 'Roselyn McLaughlin',
      tel: '(479) 706-9055 x91343',
      address: '82057 Ettie Throughway',
      opening_hours: '08:00',
      description:
        'Porro explicabo quae exercitationem sit laudantium rem voluptas in. Sit aut aut expedita modi commodi voluptate. Voluptatum aliquam iure ut.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=12.401057286026184',
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
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 47,
      name: 'Jerrold Metz',
      tel: '908.229.7303 x79812',
      address: '436 Callie Causeway',
      opening_hours: '08:00',
      description:
        'Iste voluptatum aut consequatur pariatur reiciendis perspiciatis sit odit.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.828155682682322',
      viewCounts: 0,
      createdAt: '2022-07-05T22:26:19.000Z',
      updatedAt: '2022-07-05T22:26:19.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
    {
      id: 48,
      name: 'Emmalee Dickinson',
      tel: '1-576-548-0668 x43021',
      address: '39939 Katelyn Squares',
      opening_hours: '08:00',
      description:
        'Qui recusandae cupiditate et ut voluptates et. Enim provident vero ut asperiores tenetur omnis corporis. Adipisci quas ipsam velit et sint. Repellat est facilis architecto. Sint quia dolores iusto minima qui blanditiis. Fugit nihil culpa et esse.\n \rNon expedita eaque corrupti. Nostrum non recusandae. Autem debitis neque nesciunt non non blanditiis aut recusandae ut. Non id accusamus veniam recusandae sint consequatur quod. Nesciunt et possimus eum aut ex aut et. Necessitatibus dignissimos minus provident sed quisquam eum consectetur hic saepe.\n \rCorporis minus repudiandae magni sunt earum animi soluta non id. Officia magni aut praesentium odio beatae ea porro quidem. Et perferendis et corrupti expedita ratione.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=5.4245529688122796',
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
    },
    {
      id: 49,
      name: 'Nikolas Schuster',
      tel: '060.512.5232 x374',
      address: '9835 Royal Camp',
      opening_hours: '08:00',
      description:
        'Et sit eius aut quo expedita. Fugiat expedita voluptas at enim odit perferendis. Repudiandae est laborum debitis earum consequatur ad quam.\n \rPorro qui et nemo. Natus repellat placeat fuga et qui mollitia corporis id fugit. Delectus sit doloremque. Id nihil assumenda eos necessitatibus perferendis corporis voluptatum et.\n \rEsse ut odit voluptate explicabo ex. Et architecto rem et quidem dolor consequatur earum delectus. A recusandae dolorum minima. Dolorem quia expedita sit vitae. Dolor omnis voluptatem non deleniti ipsum accusantium optio recusandae.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=32.81392081379772',
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
    },
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
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-07-05T22:26:19.000Z',
        updatedAt: '2022-07-05T22:26:19.000Z',
      },
    },
  ],
};

export default {
  name: 'AdminRestaurantsTable',
  data() {
    return {
      restaurants: [],
    };
  },
  created() {
    this.fetchRestaurants();
  },
  methods: {
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants;
    },
    deleteRestaurant(restaurantId) {
      this.restaurants = this.restaurants.filter(
        (restaurant) => restaurant.id !== restaurantId
      );
    },
  },
};
</script>
