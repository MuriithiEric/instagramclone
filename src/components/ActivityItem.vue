<template>
  <div class="activity-item">
    <div class="user-info-icon">
      <div class="inner-ctn">
        <img src="@/assets/bitmaps/profile-image.png" alt="" />
      </div>
      <div class="not-image">
        <router-link to="/profile" class="notif">
          <b>ft.muray</b> liked your comment: I am the one. that is coming for
          you <span class="notif-time">13 h</span>
        </router-link>
      </div>
    </div>
    <div v-if="even" class="subject-action image">
      <img src="@/assets/bitmaps/image1.png" alt="" />
    </div>
    <button v-else class="subject-action clear-btn">Follow</button>
  </div>
</template>

<script>
export default {
  name: "ActivityItem",
  props: {
    even: {
      type: Boolean,
      default: () => false,
    },
  },
};
</script>

<style scoped>
.activity-item {
  padding: 12px 16px;
  display: flex;
  justify-content: space-between;
}
.user-info-icon {
  display: flex;
  align-items: center;
}
.inner-ctn {
  min-height: 40px;
  min-width: 40px;
  background: radial-gradient(
    circle at 33% 100%,
    #fed373 4%,
    #f15245 30%,
    #d92e7f 62%,
    #9b36b7 85%,
    #515ecf
  );
  border-radius: 100%;
  display: grid;
  place-items: center;
}
.inner-ctn img {
  width: 32px;
  height: 32px;
  border: 2px solid #ffffff;
  object-fit: cover;
  border-radius: 50%;
}
.not-image {
  font-weight: 500;
  font-size: 0.875rem;
  margin-left: 12px;
  margin-right: 20px;
  line-height: 1.3rem;
}
.info {
  color: var(--grey-text);
  font-size: 0.75rem;
  margin-top: 2px;
}
.notif {
  text-decoration: none;
  color: #000000;
  font-weight: 400;
}
.notif-time {
  text-decoration: none;
  color: #8e8e8e;
  margin-left: 2px;
}
.subject-action.image img {
  width: 40px;
  height: 40px;
  object-fit: cover;
}
.subject-action.clear-btn {
  background: var(--blue-text);
  color: #ffffff;
  font-weight: 600;
  padding: 5px 9px;
  border-radius: 4px;
  height: 30px;
  width: 63px;
}
</style>
