<template>
  <div class="header-ctn section">
    <div class="inner">
      <router-link class="logo" to="/">
        <img src="@/assets/bitmaps/logo.png" alt="">
      </router-link>
      <div class="search-bar">
        <input type="text" placeholder="Search">
        <SearchIcon class="search-icon" />
      </div>
      <div class="quick-actions">
        <router-link to="/">
          <HomeIcon :active="$route.name === 'home'" />
        </router-link>
        <router-link to="/messages">
          <MessageIcon :active="$route.name === 'messages'" />
        </router-link>
        <button class="clear-btn" @click="setNPModalVisible(true)">
          <NewPostIcon :active="npModalVisible"/>
          <NewPostModal v-show="npModalVisible"/>
        </button>
        <router-link to="/explore">
          <ExploreIcon :active="$route.name ==='explore'" />
        </router-link>
        <button class="clear-btn" @click="setActivityModalVisibility(true)">
          <ActivityIcon :active="activityModalVisible"/>
          <ActivityModal v-show="activityModalVisible"/>
        </button>
        <button class="clear-btn profile-btn" @click="setProfileModalVisibility(true)">
          <img src="@/assets/bitmaps/profile-image.png" :class="{ active: profileModalVisible }" alt="">
          <ProfileModal v-show="profileModalVisible"/>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import HomeIcon from './HomeIcon.vue'
import SearchIcon from './SearchIcon.vue'
import MessageIcon from './MessageIcon.vue'
import NewPostIcon from './NewPostIcon.vue'
import ActivityIcon from './ActivityIcon.vue'
import ExploreIcon from './ExploreIcon.vue'
import ActivityModal from './ActivityModal.vue'
import ProfileModal from './ProfileModal.vue'
import NewPostModal from './NewPostModal.vue'
export default {
  name: 'Header',
  components: {
    HomeIcon, SearchIcon, MessageIcon, NewPostIcon, ActivityIcon, ExploreIcon,
    ActivityModal, ProfileModal, NewPostModal
  },
  computed: {
    ...mapState({
      activityModalVisible: state => state.header.activityModalVisible,
      profileModalVisible: state => state.header.profileModalVisible,
      npModalVisible: state => state.header.npModalVisible
    })
  },
  methods: {
    setActivityModalVisibility () {
      this.$store.commit('header/setActivityModalVisible', !this.activityModalVisible)
    },
    setProfileModalVisibility () {
      this.$store.commit('header/setProfileModalVisible', !this.profileModalVisible)
    },
    setNPModalVisible () {
      this.$store.commit('header/setNPModalVisible', !this.npModalVisible)
    }
  }
}
</script>

<style scoped>
.header-ctn {
  border-bottom: 1px solid var(--border-color);
  position: fixed;
  width: 100%;
  background: #FFF;
  z-index: 1;
  top: 0;
}
.header-ctn > .inner {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.header-ctn > .inner > * {
  flex-basis: 30%;
}
.header-ctn .logo {
  height: 24px;
}
.search-bar {
  position: relative;
  z-index: -1;
}
.search-bar > input {
  background: rgba(239,239,239,1);
  border: none;
  outline: none;
  height: 36px;
  width: 270px;
  max-width: 230px;
  padding: 0 8px;
  padding-left: 46px;
  border-radius: 8px;
  color: rgba(142,142,142,1);
  font-size: 1rem;
}
.search-bar > input::placeholder {
  color: rgba(142,142,142,1);
  font-weight: 300;
}
.search-bar .search-icon {
  position: absolute;
  left: 16px;
  top: 10px;
}
.quick-actions {
  display: flex;
  align-items: center;
}
.quick-actions > * {
  margin-left: 22px;
  position: relative;
  text-align: left;
}
.profile-btn {
  width: 24px;
  height: 24px;
  display: inline-block;
  background: none;
  outline: none;
  border: none;
}
.profile-btn > img {
  width: 100%;
  border-radius: 50%;
  transition: 0.3s;
}
/* .profile-btn > img.active {
  width: 100%;
  border-radius: 50%;
  border: 1px solid #262626;
} */
</style>