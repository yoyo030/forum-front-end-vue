// ./src/components/UserProfileCard.vue
<template>
<div class="card">
            <div class="card-header"><strong>{{Followers.length}}</strong> followers (追隨者)</div>
            <div class="card-body">

 
              <router-link
        v-for="followers in Followers"
        :key="followers.id"
        :to="{ name: 'user', params: { id: followers.id } }"
      >
        <img :src="followers.image" width="60" height="60" class="mr-1" />
      </router-link>

            </div>
          </div>
</template>

<script>


export default {
    name:'UserFollowersCard',  
     props: {
                Followers: {
                type: Object,
                 required: true
                }                
            }
}
</script>