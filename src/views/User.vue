<template>
  <div class="home">
    <merge-requests :merge-requests="mergeRequests" v-if="mergeRequests.length"/>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import MergeRequests from "@/components/MergeRequests.vue";
import store from "@/store";

export default {
  name: "user",
  components: {
    MergeRequests
  },
  computed: {
    ...mapGetters({
      mergeRequests: "getMergeRequests"
    })
  },
  beforeRouteEnter(to, from, next) {
    store.dispatch("loadUser", to.params.name);
    next();
  },
  beforeRouteUpdate(to, from, next) {
    store.dispatch("loadUser", to.params.name);
    next();
  }
};
</script>
