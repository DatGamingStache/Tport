<script lang="ts" setup="">
import { defineEmits, defineProps, ref, withDefaults } from 'vue'
import TechStack from '../components/TechStack.vue'
const projects = [
  {
    name: 'Pdanalytics',
    coverImg: 'pda3',
    sections: [
      { name: 'About Project', description: 'PD Analytics LLC is an education research company that specializes in helping K-12 schools to maximize their professional development spending.', components: [] },
      { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'pdanalytics' }] }] },
      { name: 'About Project', description: '', components: [] },

    ],
    link: '',
  },
  {
    name: 'Adstakr',
    coverImg: 'adstakr2',
    sections: [
      { name: 'About Project', description: 'Adstakr is a company that sells billboard AD space by time', components: [] },
      { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'adstakr' }] }] }],
    link: '',
  },
  { name: 'Big3D', coverImg: 'big3d2', sections: [{ name: 'About Project', description: 'Big3D aims to give people the ability to purchase prints on demand by submitting an stl file of aynthing that you would like printed. ', components: [] }, { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'big3d' }] }] }], link: '' },
  { name: 'BoostEhr', coverImg: 'boost', sections: [{ name: 'About Project', description: 'BoostEhr is a in house medical application for managing many processes such as Lab results, Breath Tests, Viewing Patient Survey Results, and Secure Encrypted messaging', components: [] }, { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'boostehr' }] }] }], link: '' },
  {
    name: 'Binding of Isaac: Achievements',
    coverImg: 'achievehunter',
    sections: [{ name: 'About Project', description: 'The binding of isaac achievements app was built as a twitch extension for www.twitch.tv. The goal of the app was to provide viewers and streamers a visually pleasing way to keep up with the achievements that they have earned in the game The Binding of Isaac. This project was made specifically for one game but has the ability to show achievements for any game on the steam platform', components: [] }, { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'tboi' }] }] }],
    link: '',
  },
  { name: 'Kick the Keeper', coverImg: 'ktk2', sections: [{ name: 'About Project', description: 'Kick the Keeper is an idle/clicker game designed with the binding of isaac theme in mind', components: [] }, { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'kickthekeeper' }] }] }], link: '' },
  { name: 'Crisis Cleanup', coverImg: 'cc2', sections: [{ name: 'About Project', description: 'Crisis Cleanup is a collaborative disaster work order management platform that improves coordination, reduces duplication of efforts, improves efficiency, and improves volunteers\' experience.', components: [] }, { name: 'Tech Stack', description: '', components: [{ name: TechStack, props: [{ name: 'crisiscleanup' }] }] }], link: '' },
]
const tools = [{}, {}, {}, {}, {}, {}, {}, {}, {}, {}, {}]
const display = ref(false)
const selectedItem = ref({})

// const resetProps = computed(() => {
// })
</script>

<template>
  <div
    v-if="display"
    class="bg-white w-2/3 h-2/3 shadow-xl rounded-xl  grid grid-rows-12 absolute top-50  left-50 "
  >
    <div class="bg-primary text-white rounded-t-xl shadow-xl text-center border flex items-center justify-center">
      <div class="text-4xl">
        {{ selectedItem.name }}
      </div>
    </div>
    <div class="px-4 py-2 overflow-y-auto row-span-10">
      <div v-for="(section,idx) in selectedItem.sections" :key="idx">
        <Text class="text-2xl font-bold p-4">
          {{ section.name }}
        </Text>
        <br>
        <template v-for="(block, compIdx) in section.components" :key="compIdx">
          <component :is="block.name" class="m-4" :tech-stack-name="block.props[0].name" />
        </template>
        <br>
        <Text>{{ section.description }}</Text>
        <br>
        <br>
      </div>
    </div>
    <div class="flex justify-end p-2">
      <Button class="" label="back" @click="display = false" />
    </div>
  </div>

  <div class="grid grid-cols-12" style="height: 100vh">
    <div class=" col-span-3 grid grid-cols-4 grid-rows-6 bg-primary h-full">
      <Icon name="TristonPhoto" class="h-full col-span-2" />
      <div class="text-white flex flex-col col-span-2 justify-center">
        <div class="text-2xl">
          Triston Lewis
        </div>
        <div>Web & Software Developer</div>
      </div>
      <div
        class="
          text-white
          row-end-7
          col-span-4
          flex
          items-center
          flex-col
          justify-center
        "
      >
        <div class="text-2xl">
          Contact Information
        </div>
        <div>Tony.lewis0398@gmail.com</div>
      </div>
    </div>
    <div class="col-span-9 row-span-full bg-secondary text-white grid">
      <div class="row_header">
        Projects
      </div>

      <div class="row-span-3 flex gap-4 mx-8 overflow-x-scroll overflow-y-hidden">
        <ProjectCard
          v-for="(item, idx) in projects"
          :key="idx"
          :title="item.name"
          :img="item.coverImg"
          class="w-1/3 flex-shrink-0 h-30"
          @click="(display = true), (selectedItem = item)"
        />
      </div>
      <div class="row_header">
        Tools
      </div>

      <div class="row-span-3 flex gap-4 mx-8 overflow-x-scroll">
        <ProjectCard
          v-for="(item, idx) in tools"
          :key="idx"
          :title="item.name"
          :img="item.name"
          class="w-1/3 flex-shrink-0 h-30"
        />
      </div>
      <div class="row_header">
        Languages
      </div>

      <div class="row-span-3">
        <div class="grid grid-cols-5 grid-rows-3 gap-4 mx-8">
          <Icon
            v-for="(item, idx) in [
              'css',
              'html5',
              'javascript',
              'node',
              'python',
              'react',
              'tailwind',
              'typescript',
              'vuejs',
              'ahk',
            ]"
            :key="idx"
            class="h-20 w-20 bg-white rounded-lg p-2"
            :name="'Languages/' + item"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
.row_header {
  @apply flex ml-8 mt-4 text-white text-2xl row-span-1;
}

/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  @apply bg-primary;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  @apply bg-primary;
}
</style>
