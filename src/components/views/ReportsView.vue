<template>
  <div>
    <h1
      class="text-h3 d-inline d-md-none"
      :class="[$vuetify.theme.dark ? 'white--text' : 'primary--text']"
    >
      My Report
    </h1>
    <div class="d-flex align-center">
      <h1
        class="text-h5 d-none d-md-inline"
        :class="[$vuetify.theme.dark ? 'white--text' : 'primary--text']"
      >
        My Report
      </h1>
      <v-icon class="ml-md-10">mdi-file-multiple-outline</v-icon>
      <v-icon class="ml-5 ml-md-8">mdi-share-variant</v-icon>
      <v-spacer />
      <v-expand-x-transition>
        <v-chip-group v-show="showFilters && !$vuetify.breakpoint.smAndDown">
          <v-chip
            class="transparent primary--text"
            :class="{ 'text--lighten-1': !$vuetify.theme.dark }"
            v-for="(filter, idx) in activeFilters"
            :key="idx"
          >
            <v-icon
              left
              class="primary--text"
              :class="{ 'text--lighten-1': !$vuetify.theme.dark }"
              @click="removeFilter(filter.id)"
            >
              mdi-close-circle-outline
            </v-icon>
            {{ filter.name }}
          </v-chip>
        </v-chip-group>
      </v-expand-x-transition>
      <v-icon
        @click="showFilters = !showFilters"
        class="ml-1 pa-4 transparent"
        color="primary"
      >
        mdi-filter
      </v-icon>
      <v-icon class="ml-1 pa-4">mdi-view-dashboard</v-icon>
      <v-menu
        offset-y
        left
        content-class="rounded-lg elevation-0 rounded-tr-0 background lighten-2 attached-menu__shadow"
      >
        <template #activator="{ on, value }">
          <div v-on="on">
            <v-icon
              class="ml-1 pa-4 rounded-lg cursor-pointer"
              :class="{ 'background lighten-1 rounded-b-0': value }"
            >
              mdi-view-dashboard-edit-outline
            </v-icon>
          </div>
        </template>
        <v-card class="rounded-tr-0">
          <v-list>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-download</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Export Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-share-variant</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Share Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-tune</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Report Settings </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-clock-time-four-outline</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Schedule Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-view-dashboard</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Edit Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-pin</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> Pin Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-divider />
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-chart-box-plus-outline</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> New Report </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-avatar size="22">
                <v-icon>mdi-file-document</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title> My Reports </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card>
      </v-menu>
    </div>
    <v-row>
      <v-col sm="3" v-for="i in 4" :key="i">
        <v-sheet height="150" class="accent rounded" />
      </v-col>
    </v-row>
    <v-row>
      <v-col sm="4" v-for="i in 3" :key="i">
        <v-sheet height="350" class="accent rounded" />
      </v-col>
    </v-row>
    <h1 class="text-h5 white--text my-3">New Group</h1>
    <v-row>
      <v-col sm="4">
        <v-sheet height="350" class="accent rounded" />
      </v-col>
      <v-col sm="8">
        <v-sheet height="350" class="accent rounded" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "ReportsView",
  data: () => ({
    activeFilters: [],
    showFilters: true,
    filters: [
      {
        name: "A 01 - 2022",
        id: "01to2022",
      },
      {
        name: "Age",
        id: "byAge",
      },
      {
        name: "Career",
        id: "byCareer",
      },
      {
        name: "All",
        id: "all",
      },
    ],
  }),
  methods: {
    removeFilter(id) {
      this.activeFilters = this.activeFilters.filter(
        (filter) => filter.id !== id
      );
    },
  },
  mounted() {
    // by default all filters will be applied
    this.activeFilters = this.filters;
  },
};
</script>
