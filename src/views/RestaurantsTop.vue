// ./src/views/RestaurantsTop.vue
<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>

    <hr />
    <div
      class="card mb-3"
      style="max-width: 540px; margin: auto"
      v-for="restaurant in restaurants"
      :key="restaurant.id"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img class="card-img" :src="restaurant.image" />
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              {{ restaurant.name }}
            </h5>
            <span class="badge badge-secondary"
              >收藏數：{{ restaurant.FavoriteCount }}</span
            >
            <p class="card-text">
              {{ restaurant.description }}
            </p>
            <a href="#" class="btn btn-primary mr-2">Show</a>

            <button
              type="button"
              class="btn btn-danger mr-2"
              v-if="restaurant.isFavorited"
               @click.stop.prevent="deleteLike(restaurant)"
            >
              移除最愛
            </button>
            <button type="button" class="btn btn-primary" v-else
             @click.stop.prevent="addLike(restaurant)">
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";

const dummyData = {
  restaurants: [
    {
      id: 50,
      name: "Miss Giovanni Doyle",
      tel: "1-454-196-3281 x97209",
      address: "9138 King Walks",
      opening_hours: "08:00",
      description: "Et sed rerum laudantium debitis ea in natus placea",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=38.36736584111211",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: "Miss Timmy Wolf",
      tel: "1-146-038-8870",
      address: "4823 Daugherty Pines",
      opening_hours: "08:00",
      description: "est debitis eligendi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=98.91152373491232",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: "Maye Breitenberg",
      tel: "1-807-074-4457 x2346",
      address: "5612 Fadel Summit",
      opening_hours: "08:00",
      description: "consectetur ipsa velit",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=35.66024624727571",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: "Loraine Ward",
      tel: "127-239-3235 x811",
      address: "6937 Kozey Islands",
      opening_hours: "08:00",
      description: "minus ex delectus",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=69.06766355432892",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: "Kristin West",
      tel: "046.362.5507 x5500",
      address: "1570 Kari Lodge",
      opening_hours: "08:00",
      description: "Nobis est aperiam accusantium voluptatem quo harum",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=40.78440541410209",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: "Luz Leannon",
      tel: "(240) 122-1299",
      address: "914 Abernathy Estates",
      opening_hours: "08:00",
      description: "Rerum beatae natus dolor illum cupiditate eaque. P",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=73.354362026607",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: "Lauriane Weber",
      tel: "621-680-7209 x681",
      address: "261 Rau Island",
      opening_hours: "08:00",
      description: "Rem incidunt amet facilis iure laudantium voluptat",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=34.78259954291338",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: "Ms. Madelynn Nolan",
      tel: "1-478-899-2995 x2709",
      address: "63284 Bernier Courts",
      opening_hours: "08:00",
      description: "Consequatur molestiae voluptatum hic enim dolores.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=92.67725745621127",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: "Rubie Ratke DVM",
      tel: "1-032-331-7233 x1075",
      address: "61362 Jenkins Manor",
      opening_hours: "08:00",
      description: "Perspiciatis sunt ex consectetur officia. Et in vi",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=57.117619363005545",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: "Cary Grant",
      tel: "1-684-760-4234 x497",
      address: "6600 Chaya Meadows",
      opening_hours: "08:00",
      description: "Magnam aut et et fugiat qui deserunt. Consequatur ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=19.786878850824863",
      viewCounts: 0,
      createdAt: "2022-09-15T16:02:37.000Z",
      updatedAt: "2022-09-15T16:02:37.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
};

export default {
  components: {
    NavTabs,
  },
  data() {
    return {
      restaurants: [],
    };
  },
  created() {
    this.fetchRestaurant();
  },
  methods: {
    fetchRestaurant() {
      this.restaurants = dummyData.restaurants;
    },
    addLike(restaurant) {
      restaurant.isFavorited=true;
    },
    deleteLike(restaurant) {
      restaurant.isFavorited=false;
    },
  },
};
</script>