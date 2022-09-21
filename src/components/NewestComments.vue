<template>
  <div class="card">
    <div class="card-header">最新評論</div>
    <div class="card-body">
      <div v-for="comment in comments" :key="comment.id">
        <h4>
          <router-link
            :to="{ name: 'restaurant', params: { id: comment.Restaurant.id } }"
          >
            {{ comment.Restaurant.name }}
          </router-link>
        </h4>
        <p>{{ comment.text }}</p>
        by
        <a href="#">
          {{ comment.User.name }}
        </a>
        at {{ comment.createdAt | fromNow }}
        <hr />
      </div>
    </div>
  </div>
</template>

   <script>
//import moment from 'moment'
import { fromNowFilter } from "./../utils/mixins";
export default {
  // filters: {
  //       fromNow (datetime) {
  //         if (!datetime) {
  //         return '-'
  //       }
  //       // 使用 moment 提供的 fromNow 方法
  //       return moment(datetime).fromNow()
  //       }
  //     },
  mixins: [fromNowFilter],
  props: {
    comments: {
      type: Array,
      required: true,
    },
  },
};
</script>