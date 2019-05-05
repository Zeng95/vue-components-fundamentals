<template>
  <div class="ui container">
    <div class="ui link cards">
      <GithubUserCard v-for="(username, index) in usernames" :key="index" :username="username"></GithubUserCard>
    </div>

    <Notification></Notification>

    <Notification notifHeader="Changes in Service">
      <p>We just updated our privacy policy here to better service our customers. We recommend reviewing the changes.</p>
    </Notification>

    <Notification notifType="success">
      <p>You may now log-in with the username you have chosen</p>
    </Notification>

    <Notification notifType="negative" notifHeader="We're sorry we can't apply that discount">
      <p>That offer has expired</p>
    </Notification>
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