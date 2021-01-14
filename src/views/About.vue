<template>
  <div class="about">
   <div id="page-wrap" v-if="user">
    <div id="product-details">
      <h5>{{ user.first_name }}</h5>
      <h5>{{ user.last_name }}</h5>
      <h5>{{ user.faculty }}</h5>
      <h5>{{ user.majors }}</h5>
      <h5>{{ user.email }}</h5>
      <h5>{{ user.phone_number }}</h5>
      <h5>{{ user.s_type }}</h5>
      <h5>{{ user.s_id }}</h5>
    </div>
  </div>
  <NotFoundPage v-else/>
  </div>
</template>

<script>
import axios from "axios";
import NotFoundPage from './NotFoundPage';

export default {
    name: 'ProductDetailPage',
    components: {
      NotFoundPage,
    },
    data() {
      return {
        user: {}
      };
    },
    async created() {
      const result = await axios.get(`/api/user/${this.$route.params.s_id}`);
      this.user = result.data;
    }
};
</script>

<style lang="scss" scoped></style>
