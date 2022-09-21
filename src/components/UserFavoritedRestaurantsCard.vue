<template>
    
       <div class="card">
            <div class="card-header"><strong>{{FavoritedRestaurants.length}}</strong> 收藏的餐廳</div>
            <div class="card-body">
               <router-link
        v-for="item in FavoritedRestaurants"
        :key="item.id"
        :to="{ name: 'restaurant', params: { id: item.id } }"
      >
        <img :src="item.image" width="60" height="60" class="mr-1" />
      </router-link>
            
            </div>
          </div>
</template>
<script>


export default {
    name:'UserFavoritedRestaurantsCard',
      props: {
                FavoritedRestaurants: {
                type: Array,
                required: true
                }                
            }
}
</script>
