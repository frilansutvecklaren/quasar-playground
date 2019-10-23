
<template>
  <q-layout view="hHh LpR fFf" class="layout">
    <q-header class="header">
      <div class="row no-wrap shadow-0">
        <q-toolbar class="header--toolbar">
          <q-btn
            flat
            round
            dense
            @click="left = !left"
          >
            <q-avatar rounded size="36px">
              <img src="https://cdn.quasar.dev/img/avatar2.jpg">
            </q-avatar>
            <!-- <q-badge floating color="red">3</q-badge> -->
          </q-btn>
          <q-toolbar-title style="margin-top: 5px; line-height: 16px;">
            YOU<strong>GOLF</strong><br>
            <span style="font-size: 14px;">Jane Doe</span>
          </q-toolbar-title>

          <q-space />

          <q-btn
            flat
            dense
            round
            v-if="$q.screen.width <= 1024"
            @click="right = !right"
            aria-label="Filter list"
            icon="mdi-tune"
            style="background: transparent;"
          />
        </q-toolbar>
      </div>
    </q-header>

    <q-drawer
      v-model="left"
      show-if-above
      behavior="mobile"
      :width="$q.screen.gt.xs ? 340 : 300"
      elevated
      content-class="navigation"
    >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px;">
          <q-list dark padding>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="inbox" />
              </q-item-section>

              <q-item-section>
                Inbox
              </q-item-section>
            </q-item>

            <q-item active clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="star" />
              </q-item-section>

              <q-item-section>
                Star
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="send" />
              </q-item-section>

              <q-item-section>
                Send
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="drafts" />
              </q-item-section>

              <q-item-section>
                Drafts
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/avatar2.jpg">
            </q-avatar>
            <div class="text-weight-bold">Jane Done</div>
            <div>@janedoe</div>
          </div>
        </q-img>
    </q-drawer>
    <q-drawer
      v-model="right"
      show-if-above
      :width="$q.screen.gt.xs ? 340 : 300"
      :elevated="$q.screen.width <= 1024"
      side="right"
      :breakpoint="1025"
      :content-class="`filters`"
    >
      <q-scroll-area style="height: calc(100% - 50px); margin-top: 50px;" :class="`${$q.screen.lt.md ? 'border-left' : ''}`">
      <q-list dark padding>
        <q-item-label header>General</q-item-label>

        <q-item tag="label" v-ripple>
          <q-item-section side top>
            <q-checkbox dark color="red" v-model="check1" />
          </q-item-section>

          <q-item-section>
            <q-item-label>Notifications</q-item-label>
            <q-item-label caption>
              Notify me about updates to apps or games that I downloaded
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item tag="label" v-ripple>
          <q-item-section side top>
            <q-checkbox dark color="red" v-model="check2" />
          </q-item-section>

          <q-item-section>
            <q-item-label>Sound</q-item-label>
            <q-item-label caption>
              Auto-update apps at anytime. Data charges may apply
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item tag="label" v-ripple>
          <q-item-section side top>
            <q-checkbox dark color="red" v-model="check3" />
          </q-item-section>

          <q-item-section>
            <q-item-label>Auto-add widgets</q-item-label>
            <q-item-label caption>
              Automatically add home screen widgets
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-separator spaced />

        <q-item-label header>Notifications</q-item-label>

        <q-item tag="label" v-ripple>
          <q-item-section>
            <q-item-label>Battery too low</q-item-label>
          </q-item-section>
          <q-item-section side >
            <q-toggle color="red" v-model="notif1" val="battery" />
          </q-item-section>
        </q-item>

        <q-item tag="label" v-ripple>
          <q-item-section>
            <q-item-label>Friend request</q-item-label>
            <q-item-label caption>Allow notification</q-item-label>
          </q-item-section>
          <q-item-section side top>
            <q-toggle color="red" v-model="notif2" val="friend" />
          </q-item-section>
        </q-item>

        <q-item tag="label" v-ripple>
          <q-item-section>
            <q-item-label>Picture uploaded</q-item-label>
            <q-item-label caption>Allow notification when uploading images</q-item-label>
          </q-item-section>
          <q-item-section side top>
            <q-toggle color="red" v-model="notif3" val="picture" />
          </q-item-section>
        </q-item>
      </q-list>
      </q-scroll-area>
        <q-input
          :placeholder="$t('SearchInputPlaceholderText')"
          dense
          borderless
          dark
          input-class="search-input"
          class="search-container absolute-top"
        >
          <template v-slot:append>
            <q-icon class="q-mr-sm" name="search" />
          </template>
        </q-input>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
    <!-- <q-footer class="footer text-white gt-xs">
      <q-toolbar class="footer--toolbar">
      </q-toolbar>
    </q-footer> -->
  </q-layout>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'MyLayout',
  data() {
    return {
      left: false,
      right: false,
      check1: true,
      check2: false,
      check3: false,
      notif1: true,
      notif2: true,
      notif3: false,
    }
  },
})

</script>

<style lang="scss" scoped>
.layout {
  background-color: hsl(0, 0, 12%);

  .header {
    background-color: hsla(0, 0, 10%, 1);
    .header--toolbar {
      height: 60px;
    }
  }

  .footer {
    background-color: hsla(0, 0, 11%, 1);

    .footer--toolbar {
      height: 50px;
    }
  }

  /deep/.navigation {
    background-color: hsl(0, 0, 10%);
    border-right: 1px solid hsl(0, 0, 15%);

    /deep/.navigation--item {
      height: 50px;
    }
  }

  /deep/.filters {
    background-color: hsl(0, 0, 10%);
  }

  .border-left {
    border-left: 1px solid hsl(0, 0, 15%);
  }

  .border-right {
    border-right: 1px solid hsl(0, 0, 15%);
  }

  .search-container {
    background: hsla(0, 50%, 30%, 1);
    height: 50px;
    width: 100%;

    /deep/.search-input {
      text-indent: 8px;
      background: transparent;
    }
  }
}
</style>