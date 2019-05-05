<template>
  <div class="card">
    <div class="image">
      <img :src="user.avatar_url" :alt="user.name" :title="`This is the ${user.name}'s avatar`">
    </div>

    <div class="content">
      <a :href="user.html_url" target="_blank" class="header">{{ user.name }}</a>

      <div class="meta">
        <span class="date">Joined in {{ registeredYear }}</span>
      </div>

      <div class="description">{{ user.bio }}</div>
    </div>

    <div class="extra content">
      <a :href="`https://github.com/${username}?tab=followers`" target="_blank">
        <i class="user icon"></i>
        {{ user.followers }} Friends
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    username: {
      type: String,
      required: true
    }
  },

  data() {
    return {
      user: {}
    };
  },

  computed: {
    registeredYear() {
      return new Date(this.user.created_at).getFullYear();
    }
  },

  created() {
    fetch(`https://api.github.com/users/${this.username}`)
      .then(res => res.json())
      .then(data => (this.user = data));
  }
};
</script>