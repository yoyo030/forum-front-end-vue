// ./src/components/UserProfileCard.vue
<template>
   <div class="card">
            <div class="card-header">
              <strong>{{Followings.length}}</strong> followings (追蹤者)
            </div>
            <div class="card-body">
            
             
              <router-link
        v-for="following in Followings"
        :key="following.id"
        :to="{ name: 'user', params: { id: following.id } }"
      >
        <img :src="following.image" width="60" height="60" class="mr-1" />
      </router-link>
            </div>
          </div>
</template>

<script>


export default {
    name:'UserFollowingsCard',
         props: {
                Followings: {
                type: Array,
                required: true
                }                
            }
}
</script>