<script setup lang="ts">
import LinkButton from '@/components/LinkButton.vue'

const links = [
  {
    label: 'Portfolio',
    url: 'https://stevehering.com',
    icon: 'mdi-briefcase-outline',
  },
  {
    label: 'LinkedIn',
    url: 'https://linkedin.com/in/stevehering',
    icon: 'mdi-linkedin',
  },
  {
    label: 'Email',
    url: 'mailto:steve.hering@gmail.com',
    icon: 'mdi-email-outline',
  },
]
</script>

<template>
  <v-container class="fill-height" fluid>
    <v-row justify="center" align="center" no-gutters>
      <v-col cols="12" sm="8" md="6" lg="5" xl="4">
        <v-card class="pa-8 text-center" rounded="xl" elevation="8">
          <v-avatar size="112" class="mb-4 elevation-4">
            <v-img src="/steve.jpg" alt="Steve Hering" cover />
          </v-avatar>

          <h1 class="text-h5 font-weight-bold mb-1">Steve Hering</h1>
          <p class="text-caption text-primary font-weight-medium mb-4">
            Senior Consultant, Experience Design · Slalom
          </p>
          <p class="text-body-2 text-medium-emphasis mb-6">
            Experience designer focused on healthcare, insurance, and logistics.
            I help teams illuminate new paths through complex problems and ship
            outcomes that matter.
          </p>

          <div class="d-flex flex-column ga-3">
            <LinkButton
              v-for="link in links"
              :key="link.label"
              :label="link.label"
              :url="link.url"
              :icon="link.icon"
            />

            <v-btn
              to="/about"
              prepend-icon="mdi-information-outline"
              variant="text"
              size="large"
              block
            >
              About me
            </v-btn>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
