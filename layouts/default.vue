<template>
  <v-app id="keep">
    <v-app-bar
      app
      clipped-left
      color="white"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <span class="title ml-3 mr-5">Google&nbsp;<span class="font-weight-light">Keep</span></span>

      <v-spacer />
      <sign-in />
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      color="grey lighten-4"
    >
      <v-list
        dense
        class="grey lighten-4"
      >
        <template v-for="(item, i) in items">
          <v-row
            v-if="item.heading"
            :key="i"
            align="center"
          >
            <v-col cols="6">
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-col>
            <v-col
              cols="6"
              class="text-right"
            >
              <v-btn
                small
                text
              >
                edit
              </v-btn>
            </v-col>
          </v-row>
          <v-divider
            v-else-if="item.divider"
            :key="i"
            dark
            class="my-4"
          />
          <v-list-item
            v-else
            :key="i"
            link
          >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="grey--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container
        fluid
        class="grey lighten-4 fill-height"
      >
        <v-row
          justify="center"
          align="center"
        >
          <v-col class="shrink">
            <v-tooltip right>
              <template v-slot:activator="{ on }">
                <v-btn
                  icon
                  large
                  target="_blank"
                  v-on="on"
                >
                  <v-icon large>
                    mdi-code-tags
                  </v-icon>
                </v-btn>
              </template>
              <nuxt />
            </v-tooltip>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import SignIn from '~/components/site/auth/SignIn.vue'

export default {
  components: {
    SignIn
  },
  data: () => ({
    drawer: null,
    items: [
      { icon: 'mdi-home', text: 'Notes' },
      { icon: 'mdi-home', text: 'Reminders' },
      { divider: true },
      { heading: 'Labels' },
      { icon: 'mdi-home', text: 'Create new label' },
      { divider: true },
      { icon: 'mdi-home', text: 'Archive' },
      { icon: 'mdi-home', text: 'Trash' },
      { divider: true },
      { icon: 'mdi-home', text: 'Settings' },
      { icon: 'mdi-home', text: 'Trash' },
      { icon: 'mdi-home', text: 'Help' }
    ]
  })
}
</script>

<style lang="scss" src="@/assets/styles/default.scss"/>
