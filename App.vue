<template>
  <div class="ui container">
    <div class="ui link cards">
      <GithubUserCard v-for="(username, index) in usernames" :key="index" :username="username"></GithubUserCard>
    </div>

    <Notification></Notification>
  </div>
</template>

<script>
import GithubUserCard from "./components/GithubUserCard";
import Notification from "./components/Notification";

export default {
  data() {
    return {
      usernames: ["Zeng95", "yuche", "gaearon"]
    };
  },

  components: {
    GithubUserCard,
    Notification
  }
};
</script>

<style>
@import "~semantic-ui-css/semantic.css";
</style>