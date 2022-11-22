<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
      <a class="navbar-brand" href="#">{{ title }}</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarCollapse"
        aria-controls="navbarCollapse"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="#">
              Home
              <span class="sr-only">(current)</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
        </ul>
      </div>
    </nav>
    <main role="main" class="fluid-container m-4">
      <div class="row">
        <div class="col-8">
          <div class="card mb-3" v-for="record in test" :key="record.id">
            <div class="row no-gutters" @click="favToggle(record.id)">
              <div class="col-m-4 m-2">
                <img
                  width="150px"
                  height="150px"
                  :src="hasCoverUrl(record)"
                  alt="..."
                />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">
                    {{ record.title }} ({{ record.year }})
                  </h5>
                  <p v-if="fav.includes(record.id)">😘</p>
                  <p class="card-text">{{ record.artist }}</p>
                  <p class="card-text">
                    <small class="text-muted">{{ record.comment }}</small>
                  </p>
                  <p>
                    <small>Ranked: {{ record.pitchforkPos }}</small>
                  </p>
                </div>
              </div>
            </div>
            <div
              class="card-footer"
              :class="record.stock > 0 ? 'bg-dark' : 'red'"
            >
              <small class="text-white">
                <button
                  type="button"
                  class="btn btn-info bg-transparent border-danger mr-1"
                  @click.stop="record.stock > 0 ? record.stock-- : record.stock"
                >
                  -
                </button>
                <button
                  type="button"
                  class="btn btn-info bg-transparent border-danger"
                  @click.stop="record.stock++"
                >
                  +
                </button>
                {{ getStock(record.stock) }}
              </small>
            </div>
          </div>
        </div>
        <div class="col-4">
          <div class="card bg-light mb-3" style="max-width: 18rem">
            <div class="card-header">{{ test.length }} Albums</div>
            <div class="card-body">
              <h5 class="card-title">Sort</h5>

              <p class="card-text">
                <select
                  class="custom-select"
                  v-model="sortingOption"
                  @change="sortBy"
                >
                  <option selected>Sort by:</option>
                  <option value="1">By rank (asc)</option>
                  <option value="2">By rank (desc)</option>
                  <option value="3">By year (asc)</option>
                  <option value="4">By year (desc)</option>
                </select>
              </p>
              <h5 class="card-title">Filter</h5>

              <div class="custom-control custom-switch">
                <input
                  type="checkbox"
                  class="custom-control-input"
                  id="customSwitch1"
                  @change="filterBy"
                  v-model="isChecked"
                />
                <label class="custom-control-label" for="customSwitch1"
                  >Available</label
                >
              </div>
              <div class="custom-control custom-switch">
                <input
                  type="checkbox"
                  class="custom-control-input"
                  id="customSwitch2"
                  @change="filterByK"
                  v-model="isCheckedK"
                />
                <label class="custom-control-label" for="customSwitch2"
                  >Kirby</label
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

 
<script>
import { records } from "./assets/static/js/allRecords";

export default {
  name: "App",
  components: {},
  data: () => ({
    title: "Whohoooooooo",
    records: records,
    sortingOption: "",
    filterOption: "",
    test: records,
    isChecked: false,
    isCheckedK: false,
    fav: [],
  }),
  methods: {
    hasCoverUrl(record) {
      if (record?.coverUrl) {
        return record.coverUrl;
      } else {
        return "https://giffiles.alphacoders.com/163/163324.gif";
      }
    },
    getStock(stock) {
      if (stock <= 0) {
        return "Out of stock";
      } else {
        return stock + " in stock";
      }
    },
    sortBy() {
      if (this.sortingOption == 1) {
        this.test.sort(function (a, b) {
          return a.pitchforkPos - b.pitchforkPos;
        });
      }

      if (this.sortingOption == 2) {
        this.test.sort(function (a, b) {
          return b.pitchforkPos - a.pitchforkPos;
        });
      }

      if (this.sortingOption == 3) {
        this.test.sort(function (a, b) {
          return a.year - b.year;
        });
      }

      if (this.sortingOption == 4) {
        this.test.sort(function (a, b) {
          return a.pitchforkPos - b.pitchforkPos;
        });
      }
    },

    filterBy() {
      if (this.isChecked) {
        this.test = this.records.filter((bleh) => {
          return bleh.stock < 0;
        });
      } else {
        this.test = this.records;
      }
    },

    filterByK() {
      if (this.isCheckedK) {
        this.test = this.records.filter((bleh) => {
          return bleh.title == "Double Cup";
        });
      } else {
        this.test = this.records;
      }
    },
    favToggle(id) {
      if (!this.fav.includes(id)) {
        this.fav.push(id);
      } else {
        this.fav.splice(this.fav.indexOf(id), 1);
      }
    },
  },
};
</script>

<style lang="scss">
@import "./assets/navbar-top-fixed.css";
@import "../node_modules/bootstrap/scss/bootstrap.scss";
.red {
  background-color: #ff0000;
}
.favorite {
  background-color: yellow;
}
</style>
