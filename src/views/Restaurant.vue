// ./src/views/Restaurant.vue
<template>
  <div class="container py-5">
    <h1>餐廳描述頁</h1>
    <!-- 餐廳資訊頁 RestaurantDetail -->
    <RestaurantDetail :initialRestaurant="restaurant"/>
    <hr>
    <!-- 餐廳評論 RestaurantComments -->
    <RestaurantComments :restaurantComments="restaurantComments"
    @after-delete-comment="afterDeleteComment" />
    <!-- 新增評論 CreateComment -->
    <CreateComment :restaurantId="restaurant.id" @after-create-comment="afterCreateComment"/>
  </div>
</template>

<script>
import RestaurantDetail from './../components/RestaurantDetail'
import RestaurantComments from './../components/RestaurantComments'
import CreateComment from './../components/CreateComment'
const dummyData = {
  restaurant: {
    id: 1,
    name: "Kelvin Gutmann",
    tel: "245-131-8886",
    address: "6654 Glover Oval",
    opening_hours: "08:00",
    description:
      "Sint qui odit voluptas et quod facere. Dolor mollitia voluptas laborum est sint consequatur alias. Molestiae voluptatibus fugit. Tenetur labore quia.\n \rAutem et ad maiores. Qui explicabo perferendis nulla atque. Debitis consectetur vel cumque ut qui et fuga magni.\n \rPraesentium dolores dolor facilis. Sed et veritatis perspiciatis nesciunt nisi. Ipsa earum quia fugiat explicabo illo. Laborum inventore laborum sunt est ut. Velit consequatur delectus maiores ut officiis ut repellendus necessitatibus.",
    image:
      "https://loremflickr.com/320/240/restaurant,food/?random=62.3156917148878",
    viewCounts: 1,
    createdAt: "2022-09-13T11:09:44.000Z",
    updatedAt: "2022-09-15T04:42:30.419Z",
    CategoryId: 3,
    Category: {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-09-13T11:09:44.000Z",
      updatedAt: "2022-09-13T11:09:44.000Z",
    },
    FavoritedUsers: [],
    LikedUsers: [],
    Comments: [
      {
        id: 101,
        text: "Quis facilis nihil excepturi.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$yxZosXHDLO06AVWzuAe2O.YjS0BysH3OO7RQ5sFq65yP/2qinkvPK",
          isAdmin: true,
          image: null,
          createdAt: "2022-09-13T11:09:44.000Z",
          updatedAt: "2022-09-13T11:09:44.000Z",
        },
      },
      {
        id: 51,
        text: "Culpa ullam molestiae voluptatem et et nisi eius.",
        UserId: 3,
        RestaurantId: 1,
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$y3BLrfv3X8LDUPuaHB7JKOVRPJEnN1bLegyav7UuxNUXVh5cHq6j.",
          isAdmin: false,
          image: null,
          createdAt: "2022-09-13T11:09:44.000Z",
          updatedAt: "2022-09-13T11:09:44.000Z",
        },
      },
      {
        id: 1,
        text: "Et minus omnis.",
        UserId: 1,
        RestaurantId: 1,
        createdAt: "2022-09-13T11:09:44.000Z",
        updatedAt: "2022-09-13T11:09:44.000Z",
        User: {
          id: 1,
          name: "root",
          email: "root@example.com",
          password:
            "$2a$10$yxZosXHDLO06AVWzuAe2O.YjS0BysH3OO7RQ5sFq65yP/2qinkvPK",
          isAdmin: true,
          image: null,
          createdAt: "2022-09-13T11:09:44.000Z",
          updatedAt: "2022-09-13T11:09:44.000Z",
        },
      },
    ],
  },
  isFavorited: false,
  isLiked: false,
};

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
   components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment
  },
  data () {
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
      currentUser:dummyUser.currentUser
    }
  },
  created () {
    const { id: restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant (restaurantId) {
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
    afterDeleteComment (commentId) {
      // 以 filter 保留未被選擇的 comment.id
      this.restaurantComments = this.restaurantComments.filter(
        comment => comment.id !== commentId
      )
    },
    afterCreateComment (payload) {      
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
    }
  }
}
</script>
