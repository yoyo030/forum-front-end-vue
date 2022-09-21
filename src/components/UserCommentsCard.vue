<template>
        <div class="card">
            <div class="card-header"><strong>{{Comments.length}}</strong> 已評論餐廳</div>
            <div class="card-body">           
       <router-link
        v-for="comment in Comments"
        :key="comment.id"
        :to="{ name: 'restaurant', params: { id: comment.Restaurant.id } }"
      >
        <img :src="comment.Restaurant.image" width="60" height="60" class="mr-1" />
      </router-link>

            </div>
          </div>
</template>

<script>

export default {
    name:'UserCommentsCard',
         props: {
                Comments: {
                type: Object,
                 required: true
                }                
            }
}
</script>
