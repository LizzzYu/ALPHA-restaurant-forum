<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      美食達人
    </h1>
    <hr>
    <div class="row text-center">
      <UserTopCard
        v-for="user in users"
        :key="user.id"
        :initial-user="user"
      />
      <!-- <div class="col-3">
        <a href="#">
          <img
            src="貼上引用圖片網址，同學可自行選擇圖片進行實作"
            width="140px"
            height="140px"
          >
        </a>
        <h2>User</h2>
        <span class="badge badge-secondary">追蹤人數：3</span>
        <p class="mt-3">
          <button
            type="button"
            class="btn btn-danger"
          >
            取消追蹤
          </button>
          <button
            type="button"
            class="btn btn-primary"
          >
            追蹤
          </button>
        </p>
      </div> -->
    </div>
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import UserTopCard from '../components/UserTopCard.vue'

const dummyData = {
    "users": [
        {
            "id": 1,
            "name": "root",
            "email": "root@example.com",
            "password": "$2a$10$cogesrfZKY.OZ6b2da/bRuFDmBUcrpUPAtjiSKz8joA5lDnJF09oW",
            "isAdmin": true,
            "image": null,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        },
        {
            "id": 2,
            "name": "user1",
            "email": "user1@example.com",
            "password": "$2a$10$.xp.DcsMhJvW7U2xT/DOmOXVMjSE.0LmAEqFQq8lviJqKuZJUANHu",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        },
        {
            "id": 3,
            "name": "user2",
            "email": "user2@example.com",
            "password": "$2a$10$cTp.NZ.DDAEpsYyK7AU2e.xknDEQvG38wrIVJ8KviketBvhTnj7Eq",
            "isAdmin": false,
            "image": null,
            "createdAt": "2022-07-05T22:26:19.000Z",
            "updatedAt": "2022-07-05T22:26:19.000Z",
            "Followers": [],
            "FollowerCount": 0,
            "isFollowed": false
        }
    ]
}

export default {
  components: {
    NavTabs,
    UserTopCard
  },
  data() {
    return {
      users: [],
    }
  },
  created() {
    this.fetchUsers()
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users;
    }
  }
}
</script>