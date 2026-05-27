<script setup lang="ts">
const experience = [
  {
    role: 'Senior Consultant, Experience Design',
    company: 'Slalom',
    period: 'Feb 2022 – Present',
    location: 'Columbus, Ohio',
    summary:
      'Partnering with clients across healthcare, logistics, and insurance to tackle complex business and end-user challenges — leading journey mapping, empathy mapping, and outcomes-focused design.',
  },
  {
    role: 'Manager, User Experience Design',
    company: 'Cardinal Health',
    period: 'Oct 2017 – Feb 2022',
    location: 'Columbus, Ohio',
    summary:
      'Led UX for the Enterprise Marketing team — sitemaps, user flows, wireframes, and visual design across international and U.S. properties.',
  },
  {
    role: 'Supervisor, User Experience Design',
    company: 'Cardinal Health',
    period: 'Aug 2012 – Oct 2017',
    location: 'Columbus, Ohio',
    summary:
      'Grew a UX practice and supervised designers delivering usability testing, journey mapping, and interaction design.',
  },
  {
    role: 'Senior Web Designer',
    company: 'xiik Interactive Marketing',
    period: 'Jun 2010 – Aug 2012',
    location: 'Indianapolis',
    summary: 'UI design and usability testing for interactive marketing campaigns.',
  },
  {
    role: 'Web Designer',
    company: 'Clarian Health Partners',
    period: 'May 2008 – Jun 2010',
    location: 'Indianapolis',
    summary: 'Designed web experiences for a major hospital system.',
  },
]

const skills = [
  'Journey Mapping',
  'Empathy Mapping',
  'Usability Testing',
  'User Interface Design',
  'Design Strategy',
  'Service Design',
  'Workshop Facilitation',
]
</script>

<template>
  <v-container class="py-8" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="7" xl="6">
        <v-card class="pa-6 pa-sm-8" rounded="xl" elevation="8">
          <v-btn
            to="/"
            prepend-icon="mdi-arrow-left"
            variant="text"
            size="small"
            class="mb-4"
          >
            Back
          </v-btn>

          <h1 class="text-h4 font-weight-bold">About Steve</h1>
          <p class="text-subtitle-2 text-primary mb-6">
            Senior Consultant, Experience Design · Columbus, OH
          </p>

          <p class="text-body-1 mb-4">
            I'm a designer and consultant who has spent the last decade and a half
            helping organizations make sense of complex problems and turn them into
            products and services people actually want to use. At
            <strong>Slalom</strong> I work alongside hospital systems, health
            insurance companies, and logistics organizations — illuminating new
            paths to solving their challenges and focusing on outcomes that bring
            real improvement.
          </p>
          <p class="text-body-1 mb-8">
            Before Slalom, I built and led UX teams at
            <strong>Cardinal Health</strong> for nearly a decade, with earlier stops
            in interactive marketing and hospital web design. I'm a graduate of
            <strong>Ohio Wesleyan University</strong>.
          </p>

          <h2 class="text-overline mb-3">Experience</h2>
          <v-timeline side="end" align="start" density="compact" class="mb-8">
            <v-timeline-item
              v-for="job in experience"
              :key="job.role + job.company"
              dot-color="primary"
              size="small"
            >
              <div class="d-flex justify-space-between align-baseline flex-wrap ga-2">
                <h3 class="text-subtitle-1 font-weight-bold">{{ job.role }}</h3>
                <span class="text-caption text-medium-emphasis">{{ job.period }}</span>
              </div>
              <p class="text-caption text-medium-emphasis mb-2">
                {{ job.company }} · {{ job.location }}
              </p>
              <p class="text-body-2 text-medium-emphasis">{{ job.summary }}</p>
            </v-timeline-item>
          </v-timeline>

          <h2 class="text-overline mb-3">Skills</h2>
          <div class="d-flex flex-wrap ga-2">
            <v-chip
              v-for="skill in skills"
              :key="skill"
              size="small"
              variant="tonal"
            >
              {{ skill }}
            </v-chip>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
