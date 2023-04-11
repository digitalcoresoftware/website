<template>
  <search-icon class="search__icon" colour="#0a0a0a7f" />

  <input
    class="search__bar"
    id="app-search"
    name="app-search"
    type="text"
    placeholder="Search for an app..."
    v-model="searchTerm"
    @focus="showResults = true"
    @blur="hideResults"
  />

  <div class="search__results" v-if="showResults">
    <div v-if="appSearch.length === 0">
      <div class="empty__results__wrapper">
        <no-results-icon class="no__results__icon" />

        <p>Oops, we couldn't find that app!</p>
      </div>
    </div>

    <div class="search__result__block">
      <div :class="{ mask__fade__affect: searchTerm === '' }">
        <a
          :href="app.appLink"
          v-for="app in appSearch"
          :key="app.id"
          class="app-row"
        >
          <img
            :src="require('@/assets/mock/apps/app-' + app.id + '.png')"
            :alt="app.appName + ` Logo`"
            class="app__logo"
          />

          <div class="app__info">
            <p class="app__title">{{ app.appName }}</p>
            <p class="app__description">{{ app.appDescription }}</p>
          </div>
        </a>
      </div>

      <router-link :to="{ name: 'home' }" class="see__all__link">
        See All Apps
      </router-link>
    </div>
  </div>
</template>

<script>
import searchIcon from "@/assets/icons/search-icon.vue";
import noResultsIcon from "@/assets/icons/no-results-icon.vue";

export default {
  name: "app-search",
  components: {
    searchIcon,
    noResultsIcon,
  },
  data() {
    return {
      searchTerm: "",
      showResults: false,
      apps: [
        {
          id: 1,
          appName: "oarganise",
          appDescription:
            "A comprehensive webapp designed specifically for managing and running rowing clubs. It streamlines administrative tasks such as membership management, boat reservations, event planning, and communication among members. It also offers a range of features to improve the rowing experience, such as boat tracking, training programs, and race results tracking.",
          appLink: "http://localhost:8081/",
        },
        {
          id: 2,
          appName: "SnapShare",
          appDescription:
            "A social media app for sharing photos and videos with your friends and family. You can add filters, captions, and locations to your snaps and see what your friends are up to in real-time.",
          appLink: "http://localhost:8082/",
        },
        {
          id: 3,
          appName: "MindMate",
          appDescription:
            "A mindfulness app that offers guided meditation and relaxation exercises. You can choose from a variety of sessions to help you destress, improve focus, and find inner peace.",
          appLink: "http://localhost:8083/",
        },
        {
          id: 4,
          appName: "FoodieFinder",
          appDescription:
            "A food app that helps you discover new restaurants and cuisines in your area. You can read reviews, view menus, and make reservations to plan the perfect meal.",
          appLink: "http://localhost:8084/",
        },
        {
          id: 5,
          appName: "FitFusion",
          appDescription:
            "A fitness app that offers a variety of workout programs, including yoga, HIIT, and strength training. You can customize your routine and track your progress to achieve your fitness goals.",
          appLink: "http://localhost:8085/",
        },
        {
          id: 6,
          appName: "EventEase",
          appDescription:
            "An event planning app that helps you organize and manage your next big gathering. You can create guest lists, send invitations, and track RSVPs to make sure everything goes smoothly.",
          appLink: "http://localhost:8086/",
        },
        {
          id: 7,
          appName: "TrendTrack",
          appDescription:
            "A social media app that allows you to follow the latest trends and news stories. You can customize your feed to see the topics and influencers that interest you most.",
          appLink: "http://localhost:8087/",
        },
        {
          id: 8,
          appName: "TripTonic",
          appDescription:
            "A travel app that helps you plan your next vacation. You can browse destinations, compare prices, and book flights and hotels all in one place.",
          appLink: "http://localhost:8088/",
        },
        {
          id: 9,
          appName: "DreamDash",
          appDescription:
            "A journaling app that lets you record your dreams and analyze their meaning. You can keep track of recurring themes and symbols to gain insight into your subconscious mind.",
          appLink: "http://localhost:8089/",
        },
        {
          id: 10,
          appName: "WorkWell",
          appDescription:
            "A time management app that helps you balance your work and personal life. You can set boundaries, schedule breaks, and track your progress to make sure you're achieving your goals without burning out.",
          appLink: "http://localhost:8090/",
        },
      ],
    };
  },
  computed: {
    appSearch() {
      if (this.searchTerm) {
        return this.apps.filter((app) =>
          app.appName.toLowerCase().includes(this.searchTerm.toLowerCase())
        );
      } else {
        // Shuffle the apps array using the Fisher-Yates algorithm
        let shuffled = this.apps.slice();
        let currentIndex = shuffled.length;
        let temporaryValue, randomIndex;
        while (0 !== currentIndex) {
          randomIndex = Math.floor(Math.random() * currentIndex);
          currentIndex -= 1;
          temporaryValue = shuffled[currentIndex];
          shuffled[currentIndex] = shuffled[randomIndex];
          shuffled[randomIndex] = temporaryValue;
        }

        // Return the first 5 apps from the shuffled array
        return shuffled.slice(0, 4);
      }
    },
  },
  methods: {
    hideResults() {
      setTimeout(() => {
        this.showResults = false;
      }, 200);
    },
  },
};
</script>

<style scoped>
.search__bar {
  width: 250px;
  border: none;
  background: none;
  padding-inline: 5px 15px;
}

.search__icon {
  height: 18px;
  padding-inline: 15px 5px;
}

.search__results {
  position: absolute;
  top: 45px;
  left: 0;
  right: 0;
  z-index: 100;

  background: var(--second-col);
  border-radius: 10px;
}

.empty__results__wrapper > p {
  margin-block: 0 20px;
  opacity: 0.5;
}

/* No results */
.no__results__icon {
  height: 75px;
  margin-inline: auto;
  margin-block: 10px;
}

/* App results */
.app-row {
  height: 60px;
  margin-block: 10px;
  margin-inline: 10px;
  background: var(--primary-col);
  border-radius: 5px;
  display: flex;
  align-items: center;
}

.app-row:hover {
  cursor: pointer;
}

.app__logo {
  height: 40px;
  border-radius: 5px;
  margin-inline: 10px;
}

.app__info {
  padding-inline: 5px 10px;
  text-align: left;
  color: var(--font-col);
}

.app__title {
  font-size: var(--details-txt);
}

.app__description {
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;

  font-size: var(--small-txt);
  opacity: 0.5;
}

/* See all link */
.see__all__link {
  display: block;
  margin-block: 10px;
  font-size: var(--details-txt);
  color: var(--font-col);
  opacity: 0.5;
  text-decoration: underline;
}

.see__all__link:hover {
  opacity: 1;
}
</style>
