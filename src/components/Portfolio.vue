<template>
  <v-container class="py-8" max-width="1200">
    <!-- ヘッダーセクション -->
    <div class="text-center mb-12">
      <v-avatar
        class="mb-4"
        size="120"
      >
        <v-img alt="Avatar" src="/avatar.png" />
      </v-avatar>
      <h1 class="text-h3 font-weight-bold mb-2">しーある</h1>
      <p class="text-h6 text-medium-emphasis mb-4">VRChat World Programmer</p>
      <div class="d-flex justify-center gap-2">
        <v-btn
          href="https://github.com/c-r-5"
          icon="mdi-github"
          target="_blank"
          variant="text"
        />
        <v-btn
          href="https://x.com/cs_c_r_5"
          icon="mdi-twitter"
          target="_blank"
          variant="text"
        />
        <v-btn
          href="https://vrchat.com/home/user/usr_e3966a0b-b96e-46a1-854f-dd1b2b8ac544"
          icon="mdi-virtual-reality"
          target="_blank"
          variant="text"
        />
      </div>
    </div>

    <!-- About セクション -->
    <div class="mb-12">
      <h2 class="text-h4 font-weight-bold mb-4">About</h2>
      <v-card rounded="lg" variant="tonal">
        <v-card-text class="text-body-1 pa-6" style="white-space: pre-line">
          {{ aboutText }}
        </v-card-text>
      </v-card>
    </div>

    <!-- Projects セクション -->
    <div class="mb-12">
      <h2 class="text-h4 font-weight-bold mb-4">Projects</h2>
      <v-row>
        <v-col
          v-for="project in projects"
          :key="project.title"
          cols="12"
          lg="4"
          md="6"
        >
          <v-card
            :href="project.link"
            rounded="lg"
            target="_blank"
            variant="tonal"
          >
            <v-card-item>
              <template #prepend>
                <v-avatar color="primary" size="48">
                  <v-icon>{{ project.icon }}</v-icon>
                </v-avatar>
              </template>
              <v-card-title
                class="text-wrap"
                style="overflow-wrap: break-word; word-break: break-word; white-space: normal"
              >
                {{ project.title }}
              </v-card-title>
              <v-card-subtitle>{{ project.subtitle }}</v-card-subtitle>
            </v-card-item>
            <v-card-text>
              <p class="mb-3" style="white-space: pre-line; word-break: break-word">
                {{ project.description }}
              </p>
              <v-chip-group>
                <v-chip
                  v-for="tech in project.technologies"
                  :key="tech"
                  size="small"
                  variant="outlined"
                >
                  {{ tech }}
                </v-chip>
              </v-chip-group>
            </v-card-text>
            <v-card-actions>
              <v-spacer />
              <v-icon>mdi-open-in-new</v-icon>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <!-- Skills セクション -->
    <div class="mb-12">
      <h2 class="text-h4 font-weight-bold mb-4">Skills</h2>
      <v-row>
        <v-col v-for="skill in skills" :key="skill.category" cols="12" md="6">
          <v-card rounded="lg" variant="tonal">
            <v-card-title class="d-flex align-center">
              <v-icon class="mr-2" :icon="skill.icon" />
              {{ skill.category }}
            </v-card-title>
            <v-card-text>
              <v-chip-group>
                <v-chip
                  v-for="item in skill.items"
                  :key="item"
                  class="ma-1"
                >
                  {{ item }}
                </v-chip>
              </v-chip-group>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script setup>
  const aboutText = `VRChat 向けのワールド制作を中心に活動しています。
UdonSharp を用いたゲームロジック構築やギミック実装を得意としています。`

  const projects = [
    {
      title: 'スコフィごいた Scofi-Goita',
      subtitle: 'VRChat World',
      description: `VRChat 向けのボードゲームギミックを実装。
Udon を使用してゲームロジックと UI 制御を開発しました。`,
      icon: 'mdi-checkerboard',
      link: 'https://vrchat.com/home/world/wrld_5d74d392-d90b-4b24-8da7-cdedca7965a0',
      technologies: ['UdonSharp', 'C#', 'Unity'],
    },
    {
      title: 'めたモグ - Metamogphose Lab.',
      subtitle: 'VRChat World',
      description: `Virtual Sanrio Puroland 内の育成ゲームのプログラマーとして参加。
Udon によるゲームシステムの実装を担当しました。`,
      icon: 'mdi-sprout',
      link: 'https://vrchat.com/home/world/wrld_cb8a80b2-de72-49d2-ac5d-d750f948877e',
      technologies: ['UdonSharp', 'C#', 'Unity'],
    },
  ]

  const skills = [
    {
      category: 'VRChat / Unity',
      icon: 'mdi-virtual-reality',
      items: ['UdonSharp', 'C#', 'VRChat SDK', 'Unity'],
    },
    {
      category: 'Web Development',
      icon: 'mdi-web',
      items: ['Vue.js', 'Vuetify', 'Spring', 'JavaScript'],
    },
    {
      category: 'Programming Languages',
      icon: 'mdi-code-braces',
      items: ['Python', 'Java', 'JavaScript', 'C#'],
    },
  ]
</script>
