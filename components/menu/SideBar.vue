<template>
  <v-navigation-drawer v-model="visible" :mini-variant="miniVariant" app>
    <v-list-item>
      <v-container class="d-flex justify-center">
        <v-img
          v-if="miniVariant"
          :src="logo"
          alt="Apps Logo"
          max-height="45"
          max-width="45"
        />
        <v-img
          v-else
          :src="logo"
          alt="Apps Logo"
          max-height="120"
          max-width="120"
        />
      </v-container>
    </v-list-item>
    <v-divider />
    <v-list>
      <v-list-item-group
        color="primary"
      >
        <v-list-item
          v-for="(item, i) in menus"
          :key="i"
          :to="item.to"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
    <template #append>
      <div class="pa-2 text-center">
        v1.0.0
      </div>
    </template>
  </v-navigation-drawer>
</template>
<script>
export default {
  props: {
    drawer: {
      type: Boolean,
      default: true
    },
    miniVariant: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      visible: false,
      logo: require('~/assets/images/logo.png'),
      menus: [
        { text: 'Index', icon: 'mdi-clock', to: '/' },
        { text: 'Dashboard', icon: 'mdi-account', to: '/dashboard' },
        { text: 'TV', icon: 'mdi-flag', to: '/tv' }
      ]
    }
  },
  watch: {
    drawer (v) {
      this.visible = v
      console.log(v)
    },
    visible (v) {
      this.$emit('toggle-drawer', v)
    }
  }
}
</script>
