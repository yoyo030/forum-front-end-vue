// ./src/components/UserProfileCard.vue
<template>
  <div class="card mb-3" >
  <div class="row no-gutters">
    <div class="col-md-4">
        <img src="https://i.imgur.com/iO9H3N1.png" width="300px" height="300px" />
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{profile.name}}</h5>
        <p class="card-text">
          {{profile.email}}
        </p>
        <ul class="list-unstyled list-inline">
          <li><strong>   {{profile.Comments.length}}</strong> 已評論餐廳</li>
          <li><strong>{{profile.FavoritedRestaurants.length}}</strong> 收藏的餐廳</li>
          <li><strong>{{profile.Followings.length}}</strong> followings (追蹤者)</li>
          <li><strong>{{profile.Followers.length}}</strong> followers (追隨者)</li>
        </ul>
        <p>
          
            <router-link
      :to="{ name: 'admin-user-edit', params: { id: profile.id }}" >
            <button type="submit" class="btn btn-primary">edit</button></router-link>
           
        </p>
      </div>
    </div>
  </div>
</div>
</template>

<script>


export default {
    name:'UserProfileCard',
     props: {
                profile: {
                type: Object,
                 required: true
                }                
            }
     
}
</script>