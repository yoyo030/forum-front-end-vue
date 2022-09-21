// ./src/views/Restaurants.vue
<template>
  <div class="container py-5">
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
<RestaurantsNavPills :categories="categories"/>
    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard v-for="restaurant in restaurants" :key="restaurant.id" :initialRestaurant="restaurant"/>
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
import NavTabs from './../components/NavTabs'
import RestaurantCard from './../components/RestaurantCard'
import RestaurantsNavPills from './../components/RestaurantsNavPills'
import RestaurantsPagination from './../components/RestaurantsPagination'
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Kelvin Gutmann",
      tel: "245-131-8886",
      address: "6654 Glover Oval",
      opening_hours: "08:00",
      description: "Sint qui odit voluptas et quod facere. Dolor molli",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=62.3156917148878",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Lavonne Brakus",
      tel: "1-749-457-6258",
      address: "188 Gloria Dale",
      opening_hours: "08:00",
      description: "Voluptatem velit aut atque sit eius aut. Illo est ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=38.7337386899409",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Chance Daugherty",
      tel: "296-054-4539",
      address: "5927 Dannie Crest",
      opening_hours: "08:00",
      description: "Doloribus ipsam et voluptatem itaque. Alias quibus",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=13.728418539596676",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Keon Moen",
      tel: "043-253-8431 x706",
      address: "38629 Trantow Plaza",
      opening_hours: "08:00",
      description: "Voluptate adipisci sed aut cupiditate similique de",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=68.45933870605619",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Layla Mante",
      tel: "379.432.7992 x1642",
      address: "30232 Tomas Route",
      opening_hours: "08:00",
      description: "Fugiat quas maiores neque cum sint. Enim nostrum r",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=35.072978885728205",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Billy Littel",
      tel: "358-511-7694 x701",
      address: "2767 Schuppe Port",
      opening_hours: "08:00",
      description: "Est fugit dolores.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=37.94128353556263",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Miss Dangelo Legros",
      tel: "1-513-053-8705 x0569",
      address: "05445 Mayer Flat",
      opening_hours: "08:00",
      description: "saepe",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=14.955034357168739",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "Ryley Keeling",
      tel: "121-596-6421",
      address: "7048 Elian Manor",
      opening_hours: "08:00",
      description: "Quo mollitia non cupiditate sint. Totam repellat a",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=92.71666564571548",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 2,
      Category: {
        id: 2,
        name: "日本料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Bailey Casper",
      tel: "897.460.8894",
      address: "2338 Kali Ramp",
      opening_hours: "08:00",
      description: "Est in illum cumque ea aut earum ipsum. Doloribus ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=52.36126587400833",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Marcelina Franecki",
      tel: "(572) 470-4274 x870",
      address: "634 Harris Lodge",
      opening_hours: "08:00",
      description: "iste non eos",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=89.1293060854593",
      viewCounts: 0,
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  name:'restaurants',
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination
  },
  data () {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1

    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants () {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next
      } = dummyData
      this.restaurants = restaurants
      this.categories = categories
      this.categoryId = categoryId
      this.currentPage = page
      this.totalPage = totalPage
      this.previousPage = prev
      this.nextPage = next
    }

  }
}
</script>