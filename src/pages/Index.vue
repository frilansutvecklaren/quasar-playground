<template>
  <q-page flex class="reviews-page" :style-fn="pageStyle">
    <q-page-sticky position="top" expand style="z-index: 1;">
      <div class="row" style="width: 100%">
        <q-toolbar class="reviews-page--list-toolbar text-white">
          <q-toolbar-title>
            {{ $t('reviews') }}
          </q-toolbar-title>

          <q-space />

          <q-btn flat round dense icon="view_list" />
          <q-btn flat round dense icon="apps" />
        </q-toolbar>
      </div>
    </q-page-sticky>

    <q-list dark class="reviews-list">
      <q-item v-for="n in 40" class="review-item" :key="`review-${n}`">
        <q-item-section avatar center>
          <q-icon name="fab fa-github" color="white" size="34px" />
        </q-item-section>

        <q-item-section center class="col-2 gt-sm">
          <q-item-label class="">GitHub</q-item-label>
        </q-item-section>

        <q-item-section center>
          <q-item-label lines="1">
            <span class="text-weight-medium">[quasarframework/quasar]</span>
            <span class="text-grey-8"> - GitHub repository</span>
          </q-item-label>
          <q-item-label caption lines="1">
            @rstoenescu in #3: > Generic type parameter for props
          </q-item-label>
          <!-- <q-item-label lines="1" class="q-mt-xs text-body2 text-weight-bold text-blue-grey-6 text-uppercase">
            <span class="cursor-pointer">Open in GitHub</span>
          </q-item-label> -->
        </q-item-section>

        <q-item-section center class="col-3 gt-xs">
          <q-item-label lime="1">
            <q-rating
              :value="randomRating()"
              size="2em"
              color="orange"
              readonly
            />
          </q-item-label>
        </q-item-section>

        <q-item-section center side>
          <div class="text-grey-8 q-gutter-xs">
            <q-btn class="gt-xs" size="12px" flat dense round icon="delete" />
            <q-btn class="gt-xs" size="12px" flat dense round icon="done" />
            <q-btn size="12px" flat dense round icon="more_vert" />
          </div>
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'PageIndex',
  data: () => ({
    items: [],
    ratingModel: 3.5,
  }),
  components: {},
  computed: {
    pageStyle() {
      return {
        paddingTop: '50px'
      }
    }
  },
  methods: {
    randomRating() {
      return Math.random() * (5 - 1) + 1;
    }
  }
});

</script>

<style lang="scss" scoped>
  .reviews-page {
    padding-top: 50px;

    /deep/.reviews-page--list-toolbar {
      background-color: hsla(0, 50%, 50%, 1);
    }
    .reviews-list {
      .review-item {
        border-bottom: 1px solid hsl(0, 0, 10%)
      }
      .review-item:nth-child(even) {
        background-color: hsl(0, 0, 13%);
      }
    }
  }
</style>