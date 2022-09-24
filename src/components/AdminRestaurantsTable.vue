// ./src/components/AdminRestaurantsTable.vue
<template>
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th scope="col">
          #
        </th>
        <th scope="col">
          Category
        </th>
        <th scope="col">
          Name
        </th>
        <th
          scope="col"
          width="300"
        >
          操作
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="restaurant in restaurants"
        :key="restaurant.id"
      >
        <th scope="row">
          {{ restaurant.id }}
        </th>
        <td>{{ restaurant.Category ? restaurant.Category.name : '未分類' }}</td>
        <td>{{ restaurant.name }}</td>
        <td class="d-flex justify-content-between">
          <router-link :to="{name: 'admin-restaurant', params: {id: restaurant.id}}" class="btn btn-link">
  Show
</router-link>

          <router-link :to="{name: 'admin-restaurant-edit', params: {id: restaurant.id}}"
            href="#"
            class="btn btn-link"
          >Edit</router-link>

          <button
            type="button"
            class="btn btn-link"
            @click.stop.prevent="deleteRestaurant(restaurant.id)"
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
      "id": 1,
      "name": "Louie Kunze",
      "tel": "1-188-499-8185",
      "address": "6875 Brekke Brook",
      "opening_hours": "08:00",
      "description": "Qui minus quis dolore alias et. Dolor ut et.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.923558837625905",
      "viewCounts": 2,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-16T15:29:42.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 2,
      "name": "Dahlia Ankunding",
      "tel": "052.465.8024",
      "address": "75167 Nichole Freeway",
      "opening_hours": "08:00",
      "description": "Et cumque doloremque dignissimos provident quis.\nEst porro eum accusamus animi neque maiores.\nUnde ipsam molestiae corporis at temporibus ad.\nId rerum amet ut tempore dolores est ea provident atque.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=44.43780352485172",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 3,
      "name": "Korey Will",
      "tel": "975-772-7758",
      "address": "179 Hansen Roads",
      "opening_hours": "08:00",
      "description": "consequatur et corporis",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=76.23545314339677",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 4,
      "name": "Chandler O'Hara",
      "tel": "1-522-981-1260 x03892",
      "address": "09884 Considine Island",
      "opening_hours": "08:00",
      "description": "Aspernatur fuga rem consectetur tempore consequatur facilis voluptas et. Neque earum minima delectus in praesentium eos ea doloribus.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.41272690573818",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 5,
      "name": "Janick Gottlieb",
      "tel": "(906) 612-9105",
      "address": "49087 Henry Forges",
      "opening_hours": "08:00",
      "description": "Non reiciendis odit ullam voluptatibus est qui impedit doloribus aut. Et minus omnis debitis provident voluptatibus consequatur nostrum similique. Veniam nihil illum excepturi. Numquam fugiat ut hic eligendi totam nulla voluptates et. Velit excepturi dolore esse quisquam beatae voluptatibus.\n \rCupiditate delectus non eaque ut. Voluptas voluptas dolore. Culpa doloribus qui omnis temporibus sunt.\n \rMolestiae eum a aut est porro aliquid quas eum quibusdam. Consequatur dolorum omnis libero. Quas earum quis architecto dolore qui perferendis totam qui. Suscipit animi aliquam facere aliquid distinctio quas enim vel vero. Aut aut beatae nesciunt sit recusandae.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=96.93654185389855",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 6,
      "name": "Ana Hane III",
      "tel": "(802) 367-9755",
      "address": "4194 Runolfsdottir Center",
      "opening_hours": "08:00",
      "description": "Dolor reprehenderit enim libero neque. Voluptas laudantium provident et incidunt est deserunt nemo ratione. Perferendis doloremque repellendus nesciunt modi sunt aut.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=45.082407152851964",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 7,
      "name": "Raquel Doyle",
      "tel": "(105) 753-6547",
      "address": "95707 Dwight Shore",
      "opening_hours": "08:00",
      "description": "omnis",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=84.03043124527738",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 8,
      "name": "Fidel Deckow",
      "tel": "020.179.8560 x86472",
      "address": "094 Eula Plaza",
      "opening_hours": "08:00",
      "description": "Nam dolor tempora deserunt. Animi commodi dolores unde occaecati inventore qui blanditiis rerum rerum. Cupiditate minus velit ut repellat perspiciatis sint autem et amet. Et adipisci autem libero quo et fugit optio. Nesciunt voluptas saepe eos similique harum id qui id. Ea itaque dignissimos quae aut.\n \rConsectetur facere nam illo dolorum id sed dolore. Dignissimos facilis et quia atque distinctio quam. Asperiores sint quia veniam rem. Alias sit delectus.\n \rNecessitatibus facere corporis quo et. Nesciunt molestias omnis omnis beatae officia. Esse sit vel nisi ratione inventore voluptatem. Laboriosam repudiandae corrupti molestiae inventore. Rerum non non nisi aut expedita. Sunt rerum corporis tenetur veniam.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=16.53900261141832",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 9,
      "name": "Rafael Reinger",
      "tel": "311.549.8948",
      "address": "86884 Dorcas Extensions",
      "opening_hours": "08:00",
      "description": "Fugit debitis non itaque reiciendis velit nihil sequi labore inventore.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=61.59790276399855",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 10,
      "name": "Benedict Reilly",
      "tel": "156-581-9459 x65546",
      "address": "85726 Hand Stravenue",
      "opening_hours": "08:00",
      "description": "rerum voluptas veritatis",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=15.711995305218696",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 11,
      "name": "Chelsie Rutherford",
      "tel": "1-100-243-9262 x400",
      "address": "185 Lockman Place",
      "opening_hours": "08:00",
      "description": "expedita",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=24.639573992594222",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 12,
      "name": "Jeanette Pagac",
      "tel": "476.318.2701 x59632",
      "address": "3683 Brandyn Flat",
      "opening_hours": "08:00",
      "description": "Eligendi dicta iure veniam pariatur quod ullam.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=45.69900033747651",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 13,
      "name": "Julian Koelpin",
      "tel": "113-844-3706 x565",
      "address": "0750 Jacobi Knoll",
      "opening_hours": "08:00",
      "description": "Quo optio consectetur iure necessitatibus voluptate ut dolores voluptate.\nPossimus saepe aut magni commodi inventore minima nihil iure.\nEst blanditiis impedit.\nQui vel porro blanditiis et optio.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.32810617910394",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 14,
      "name": "Ms. Dock Stracke",
      "tel": "1-118-368-2436",
      "address": "059 Littel Lodge",
      "opening_hours": "08:00",
      "description": "Ratione ipsa aliquam alias. Et voluptas non eaque nesciunt consequatur voluptas dignissimos maiores quo. Explicabo voluptate ipsa numquam. Voluptatem facere voluptates et quisquam. Consectetur in temporibus fuga facere voluptates. Iste beatae sunt temporibus magnam et eum.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=41.86611332352588",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 15,
      "name": "Brice Haley",
      "tel": "791.375.2301 x1958",
      "address": "5065 Weissnat Squares",
      "opening_hours": "08:00",
      "description": "Aut cupiditate totam vel qui id molestiae et iure. Possimus est et eos rerum et voluptatum saepe. Est hic temporibus accusamus. Exercitationem libero praesentium qui tempora qui natus. Dolor aliquam veniam et impedit reprehenderit deleniti in tenetur suscipit. Nihil dignissimos ad distinctio qui.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=49.44548466865757",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 16,
      "name": "Jerome Runte",
      "tel": "1-421-366-8334",
      "address": "7738 Candido Union",
      "opening_hours": "08:00",
      "description": "Iure amet nisi. Deleniti nesciunt ratione mollitia. Dolor enim animi ab labore. Ut sed est. Dolor omnis consectetur ut provident ab. Temporibus voluptatum ipsa.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=31.32538825292077",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 17,
      "name": "Mr. Ocie Lesch",
      "tel": "1-861-811-4200 x965",
      "address": "4593 Vernon Parks",
      "opening_hours": "08:00",
      "description": "Nesciunt adipisci dolores consequatur eos maxime dolorum quis veritatis sequi. Occaecati fuga debitis beatae ipsa ipsam mollitia. Architecto quam maiores sunt omnis. Deserunt fugit et quia explicabo dolor expedita dolorum non. Temporibus sit quo temporibus est id ut voluptate quis dolore. Officiis porro fugit molestiae quia in incidunt.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=97.88552468855072",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 18,
      "name": "Miss Mohamed Pouros",
      "tel": "(176) 403-3323 x62475",
      "address": "30608 Lesch Turnpike",
      "opening_hours": "08:00",
      "description": "aperiam",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=72.38081123308038",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 19,
      "name": "Shayne Konopelski",
      "tel": "537-249-9270 x46771",
      "address": "8399 Raina Coves",
      "opening_hours": "08:00",
      "description": "Sed voluptatibus at sunt incidunt molestiae eum facilis. Qui sed dolores sunt. Ea esse architecto vel quia nesciunt ex odit quae. Pariatur illum molestiae vitae vel cumque labore ut delectus.\n \rNostrum debitis rerum saepe. Necessitatibus nulla inventore et aliquam quia. Quis iusto ullam natus aut non rerum est odit cum. Eligendi officia quia nostrum asperiores.\n \rUt laboriosam non nostrum fuga doloremque. Earum consequatur consequatur est error. Qui dolorem omnis aspernatur nobis et nobis.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=95.28262984740168",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 20,
      "name": "Tod Flatley",
      "tel": "540-368-3234 x280",
      "address": "17110 Concepcion Well",
      "opening_hours": "08:00",
      "description": "fugiat",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=81.96917258740169",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 21,
      "name": "Yoshiko Gislason",
      "tel": "108.454.4096 x841",
      "address": "24345 Wyman River",
      "opening_hours": "08:00",
      "description": "Quia eligendi eos labore qui quibusdam quasi molestiae quisquam repudiandae. Omnis iusto est consequatur nostrum repellendus aut.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=8.240457000394263",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 22,
      "name": "Clarabelle Wiegand",
      "tel": "406-733-8474",
      "address": "39550 Ariane Station",
      "opening_hours": "08:00",
      "description": "beatae sequi nihil",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=52.874871475843776",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 23,
      "name": "Ms. Karen Pfeffer",
      "tel": "(009) 566-4526",
      "address": "592 Fadel Knolls",
      "opening_hours": "08:00",
      "description": "ut sit sint",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=88.88970063886737",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 24,
      "name": "Madge Leffler",
      "tel": "1-758-244-6837",
      "address": "9573 Harry Plains",
      "opening_hours": "08:00",
      "description": "Ad numquam asperiores qui et. Velit dolorem ab ratione laudantium aut aut dolores. Amet est ipsa facilis enim. Qui suscipit quia et. Saepe adipisci non porro accusantium ipsa laudantium. Iusto eaque amet exercitationem ratione mollitia.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=80.17581085596817",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 25,
      "name": "Ross Langosh",
      "tel": "998.720.2310",
      "address": "663 Herman Court",
      "opening_hours": "08:00",
      "description": "Vel sint est qui itaque ut dolore cupiditate eveniet. Quod qui et est quas similique necessitatibus error alias possimus. Rerum autem qui veritatis aliquid quibusdam modi. Ducimus voluptatibus praesentium.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=88.26504844721117",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 26,
      "name": "Molly D'Amore",
      "tel": "1-221-559-3756 x118",
      "address": "513 VonRueden Mount",
      "opening_hours": "08:00",
      "description": "Aliquam nobis qui vitae inventore in. Vel eum nostrum. Quis a mollitia minus occaecati illo quam. Enim culpa nobis molestiae est ea. Recusandae sunt dolor recusandae fuga quia.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=73.65912982899904",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 27,
      "name": "Evalyn McClure",
      "tel": "1-335-058-0031",
      "address": "773 Lennie Island",
      "opening_hours": "08:00",
      "description": "Mollitia eaque consequatur cum maiores eos qui iure aliquam.\nEos dolorem impedit.\nDicta modi molestiae quo voluptatibus repudiandae voluptas accusantium corrupti.\nQuidem ullam vitae facilis rerum eos ipsa ipsum.\nEst laborum mollitia ullam ut dolorem unde error error vero.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=28.90828849958862",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 28,
      "name": "Izabella McDermott",
      "tel": "078.261.8002",
      "address": "89646 Malcolm Well",
      "opening_hours": "08:00",
      "description": "sunt",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=61.71562681806579",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 29,
      "name": "Elisha Nienow",
      "tel": "1-508-735-5916",
      "address": "8746 Walton Loaf",
      "opening_hours": "08:00",
      "description": "eveniet",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.97155048225736",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 30,
      "name": "Lamar Becker IV",
      "tel": "947.855.9138",
      "address": "14613 Skiles Landing",
      "opening_hours": "08:00",
      "description": "Rem repudiandae beatae reprehenderit ut qui.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=22.152718465542588",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 31,
      "name": "Reece Mayert",
      "tel": "(898) 715-3225",
      "address": "25927 Sawayn Circles",
      "opening_hours": "08:00",
      "description": "amet",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=89.540731499164",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 32,
      "name": "Melody Welch",
      "tel": "714.653.2256 x89988",
      "address": "2032 Swift Square",
      "opening_hours": "08:00",
      "description": "Qui nulla odit. Et consequuntur fuga et ipsam temporibus libero voluptatem tenetur ipsam. Ea omnis fuga perspiciatis expedita. Quasi dicta eius. Ipsam nulla rerum laborum sed est.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=39.79770452896447",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 33,
      "name": "Dr. Fausto Runte",
      "tel": "833.421.4718 x097",
      "address": "416 Leif Summit",
      "opening_hours": "08:00",
      "description": "Iure maiores laudantium modi aspernatur nobis rerum aliquid. Et quasi deserunt iure suscipit non iusto voluptas. Aut est aut minus sed enim. Sit nemo architecto explicabo ipsum sit aut dolores excepturi. Error sunt sit quo qui. Cum ab sit earum minus sapiente tempore.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=24.834566912913168",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 34,
      "name": "Ruthie Carroll",
      "tel": "1-989-921-0517 x03964",
      "address": "039 Eichmann Turnpike",
      "opening_hours": "08:00",
      "description": "iusto",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=87.324018606072",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 35,
      "name": "Megane Dickens",
      "tel": "(375) 144-2337 x06473",
      "address": "253 Dagmar Light",
      "opening_hours": "08:00",
      "description": "Nam magni est aut ut vel architecto et temporibus.\nEnim eos velit at harum et tempore pariatur.\nIpsa laudantium accusantium aliquid.\nQuibusdam nostrum sunt amet sit qui.\nNon illo ducimus et voluptatem dolorem natus qui cumque nesciunt.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=18.7158349644718",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 36,
      "name": "Dr. Missouri Beatty",
      "tel": "1-737-855-9052",
      "address": "36156 McDermott Wall",
      "opening_hours": "08:00",
      "description": "Sunt voluptatum saepe nihil modi. Voluptas beatae quis voluptatem dolor. Est voluptas velit cum hic impedit et iusto. Sed facere qui. Explicabo expedita aut repellat voluptatum eligendi rerum vitae et. Explicabo laborum consequatur.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=2.5700977747334486",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 37,
      "name": "Theo Will",
      "tel": "1-527-562-9737",
      "address": "70545 Jacobi Walks",
      "opening_hours": "08:00",
      "description": "Ut eveniet temporibus optio possimus. Veritatis voluptatem nobis ducimus rem quidem quidem excepturi ut. Animi quia quas rerum eveniet molestias omnis. Dolorem quaerat libero vel beatae blanditiis non. Quo consequatur at quae sit commodi deleniti et.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=68.64868239210486",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 38,
      "name": "Cassidy Gleichner",
      "tel": "(663) 478-1785",
      "address": "31025 Brown Burg",
      "opening_hours": "08:00",
      "description": "nostrum",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=53.64129446736674",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 39,
      "name": "Darren Koch III",
      "tel": "1-294-418-9769",
      "address": "1864 Hickle Mills",
      "opening_hours": "08:00",
      "description": "Maiores ipsam esse ad esse deserunt eligendi nulla.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=65.99159566527497",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 5,
      "Category": {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 40,
      "name": "Johann Grant",
      "tel": "1-457-756-8115 x8982",
      "address": "5515 Stacy Loop",
      "opening_hours": "08:00",
      "description": "Sapiente porro amet adipisci rerum.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=51.033529930976606",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 41,
      "name": "Cary Grant",
      "tel": "1-684-760-4234 x497",
      "address": "6600 Chaya Meadows",
      "opening_hours": "08:00",
      "description": "Magnam aut et et fugiat qui deserunt. Consequatur dignissimos similique et reiciendis sequi voluptates. Molestias cupiditate et eius.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=19.786878850824863",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 42,
      "name": "Rubie Ratke DVM",
      "tel": "1-032-331-7233 x1075",
      "address": "61362 Jenkins Manor",
      "opening_hours": "08:00",
      "description": "Perspiciatis sunt ex consectetur officia. Et in vitae sapiente. Ea at iste.\n \rFugiat qui voluptatum reprehenderit ut odit exercitationem iste illo. Ad debitis doloribus facilis est minus error. Sint omnis est sed ipsum perferendis iste aspernatur dolorum.\n \rQuae accusamus sunt ipsum ut. Est omnis et quo minus voluptatibus dolorem quia repudiandae. Maxime doloribus facilis laudantium natus atque quia et quis minus.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=57.117619363005545",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 43,
      "name": "Ms. Madelynn Nolan",
      "tel": "1-478-899-2995 x2709",
      "address": "63284 Bernier Courts",
      "opening_hours": "08:00",
      "description": "Consequatur molestiae voluptatum hic enim dolores.\nQuia libero voluptatibus.\nEst deleniti et eligendi sapiente.\nDolor eaque repellat est nihil vel.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=92.67725745621127",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 44,
      "name": "Lauriane Weber",
      "tel": "621-680-7209 x681",
      "address": "261 Rau Island",
      "opening_hours": "08:00",
      "description": "Rem incidunt amet facilis iure laudantium voluptatem velit. Et sit eum incidunt.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.78259954291338",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 1,
      "Category": {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 45,
      "name": "Luz Leannon",
      "tel": "(240) 122-1299",
      "address": "914 Abernathy Estates",
      "opening_hours": "08:00",
      "description": "Rerum beatae natus dolor illum cupiditate eaque. Placeat voluptas blanditiis aliquid aliquid perspiciatis sed est fugit dolorem. Tempore et nisi est. Eum officiis hic voluptate qui voluptates animi.\n \rVoluptatem cupiditate corrupti quia assumenda rem ad quia tempora. Aut odit saepe. Nisi ad minima ea inventore quidem voluptatem reprehenderit consequuntur in.\n \rDolores itaque sapiente facilis tenetur. Dolorem est recusandae accusamus suscipit non optio enim. Minus eum ducimus repellat. Consectetur rem odit.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=73.354362026607",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 46,
      "name": "Kristin West",
      "tel": "046.362.5507 x5500",
      "address": "1570 Kari Lodge",
      "opening_hours": "08:00",
      "description": "Nobis est aperiam accusantium voluptatem quo harum optio qui. Nesciunt doloremque nemo eos ex eaque iste veritatis accusantium. Deleniti incidunt dolorem culpa nesciunt ipsum sit consequatur enim ut. Qui sed asperiores.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=40.78440541410209",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 47,
      "name": "Loraine Ward",
      "tel": "127-239-3235 x811",
      "address": "6937 Kozey Islands",
      "opening_hours": "08:00",
      "description": "minus ex delectus",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=69.06766355432892",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 4,
      "Category": {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 48,
      "name": "Maye Breitenberg",
      "tel": "1-807-074-4457 x2346",
      "address": "5612 Fadel Summit",
      "opening_hours": "08:00",
      "description": "consectetur ipsa velit",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=35.66024624727571",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 49,
      "name": "Miss Timmy Wolf",
      "tel": "1-146-038-8870",
      "address": "4823 Daugherty Pines",
      "opening_hours": "08:00",
      "description": "est debitis eligendi",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=98.91152373491232",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 3,
      "Category": {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    },
    {
      "id": 50,
      "name": "Miss Giovanni Doyle",
      "tel": "1-454-196-3281 x97209",
      "address": "9138 King Walks",
      "opening_hours": "08:00",
      "description": "Et sed rerum laudantium debitis ea in natus placeat minus.\nUllam omnis voluptas enim doloremque sequi reprehenderit dolor.\nAnimi explicabo voluptatibus totam corrupti quaerat ea corrupti quod iusto.\nLaboriosam et quas corporis.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=38.36736584111211",
      "viewCounts": 0,
      "createdAt": "2022-09-15T16:02:37.000Z",
      "updatedAt": "2022-09-15T16:02:37.000Z",
      "CategoryId": 2,
      "Category": {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2022-09-15T16:02:37.000Z",
        "updatedAt": "2022-09-15T16:02:37.000Z"
      }
    }
  ]
}

export default {
  data () {
    return {
      restaurants: []
    }
  },
  created () {
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants () {
      this.restaurants = dummyData.restaurants
    },
     deleteRestaurant (restaurantId) {
      this.restaurants = this.restaurants.filter(
        restaurant => restaurant.id !== restaurantId
      )
    }
  }
}
</script>