<script>
import { mapGetters } from 'vuex'
import UpgradeBadge from '@/components/UpgradeBadge'

export default {
  components: {
    UpgradeBadge
  },
  data() {
    return {
      model: false
    }
  },
  computed: {
    ...mapGetters('api', ['isCloud']),
    ...mapGetters('license', ['hasPermission'])
  }
}
</script>

<template>
  <v-menu
    v-model="model"
    offset-y
    transition="slide-y-transition"
    nudge-bottom="25"
  >
    <template #activator="{on}">
      <v-btn
        :input-value="$route.path.includes('/team/')"
        class="text-subtitle-1 text-capitalize mx-1 font-weight-medium"
        dark
        small
        depressed
        color="transparent"
        title="Open the team menu"
        v-on="on"
      >
        Team
      </v-btn>
    </template>

    <v-sheet width="400" class="white">
      <v-list>

        <v-list-item :to="'/team/cloud-hooks'">
          <v-list-item-avatar tile>
            <i class="o-100 fad fa-clouds fa-2x" />
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="text-subtitle-1">
              Cloud Hooks
            </v-list-item-title>
            <v-list-item-subtitle>
              Create and modify team-wide Cloud Hooks
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list-item :to="'/team/flow-groups'">
          <v-list-item-avatar tile>
            <v-icon large color="navIcons">
              pi-flow
            </v-icon>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="text-subtitle-1">
              Flow Groups
            </v-list-item-title>
            <v-list-item-subtitle>
              View all your team's flows
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list-item :to="'/team/actions'">
          <v-list-item-avatar>
            <span class="auto-icon">
              <i class="fad fa-random" style="width: 24px; height: 24px;"></i>
            </span>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>Automation Actions</v-list-item-title>
            <v-list-item-subtitle>
              View and manage automation actions
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list-item :to="'/team/projects'">
          <v-list-item-avatar tile>
            <v-icon large color="navIcons">
              pi-project
            </v-icon>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="text-subtitle-1">
              Projects
            </v-list-item-title>
            <v-list-item-subtitle>
              Create and modify your team's projects
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

      </v-list>
    </v-sheet>
  </v-menu>
</template>

<style lang="scss" scoped>
$dark-grey-icon: var(--v-navIcons-base);
$dark-blue-icon: var(--v-primaryDark-base);

.o-100 {
  &.svg-inline--fa {
    --fa-primary-opacity: 0.8;
    --fa-secondary-opacity: 0.8;
  }
}

.fa-abacus {
  --fa-primary-color: #{$dark-grey-icon};
  --fa-secondary-color: #{$dark-blue-icon};
}

.fa-random {
  --fa-primary-color: #{$dark-grey-icon};
  --fa-secondary-color: #{$dark-blue-icon};
}

.fa-key-skeleton {
  --fa-primary-color: #{$dark-blue-icon};
  --fa-secondary-color: #{$dark-grey-icon};
}

.fa-users {
  --fa-primary-color: #{$dark-blue-icon};
  --fa-secondary-color: #{$dark-grey-icon};
}

.fa-user-hard-hat {
  --fa-primary-color: #{$dark-blue-icon};
  --fa-secondary-color: #{$dark-grey-icon};
}

.fa-clouds {
  --fa-primary-color: #{$dark-blue-icon};
  --fa-secondary-color: #{$dark-grey-icon};
}

.fa-exchange-alt {
  --fa-primary-color: #{$dark-blue-icon};
  --fa-secondary-color: #{$dark-grey-icon};
}

/* stylelint-disable-next-line */
.v-list-item--disabled {
  /* stylelint-disable-next-line */
  .v-list-item__avatar {
    opacity: 0.25 !important;
  }

  /* stylelint-disable-next-line */
  .v-list-item__subtitle {
    opacity: 0.4 !important;
  }
}
</style>
