
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
            class="mobile-only"
            @click="right = !right"
            aria-label="Filter list"
            icon="s_filter_list"
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
      <q-list dark>
        <q-item style="height: 50px;">
          <q-item-section center>
            <q-item-label style="font-size: 21px;">YOU<strong>GOLF</strong></q-item-label>
          </q-item-section>
          <q-item-section center side>
            <q-btn
              flat
              dense
              round
              @click="left = !left"
              aria-label="Close"
              icon="close"
            />
          </q-item-section>
        </q-item>
        <q-item class="q-mt-xs" clickable tag="a" target="_blank" rel="noopener" href="http://quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_school" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Docs</q-item-label>
            <q-item-label caption>https://quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" rel="noopener" href="https://github.quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Github</q-item-label>
            <q-item-label caption>github.com/quasarframework</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" rel="noopener" href="http://chat.quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_chat" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Discord Chat Channel</q-item-label>
            <q-item-label caption>https://chat.quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" rel="noopener" href="https://forum.quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_record_voice_over" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Forum</q-item-label>
            <q-item-label caption>https://forum.quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" rel="noopener" href="https://twitter.quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_rss_feed" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Twitter</q-item-label>
            <q-item-label caption>@quasarframework</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" rel="noopener" href="https://facebook.quasar.dev">
          <q-item-section avatar>
            <q-icon name="o_public" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Facebook</q-item-label>
            <q-item-label caption>@QuasarFramework</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>
    <q-drawer
      v-model="right"
      show-if-above
      :width="$q.screen.gt.xs ? 340 : 300"
      :elevated="$q.platform.is.mobile"
      side="right"
      content-class="filters"
    >
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
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
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
    background-color: hsl(0, 0, 12%);
    .header--toolbar {
      height: 60px;
    }
  }

  /deep/.navigation {
    background-color: hsl(0, 0, 10%);
    border-right: 1px solid hsl(0, 0, 20%);

    /deep/.navigation--item {
      height: 50px;
    }
  }

  /deep/.filters {
    background-color: hsl(0, 0, 10%);
    border-left: 1px solid hsl(0, 0, 20%);
  }
}
</style>