<template>
  <v-hover>
    <template #default="{ isHovering, props }">
      <div v-bind="props" class="flex items-center gap-3 pt-1 pb-2 rounded-[20px] px-2 select-none"
        :class="theme === 'customLightTheme' ? 'bg-white/50' : 'bg-black/50'">
        <!-- Bottom icons -->
        <div class="flex flex-col items-center justify-center relative" v-for="image in images" :key="image?.id">
          <v-img :src="image?.logo" :aspect-ratio="1" :width="image?.width" class="mb-1" />

          <div v-if="image?.active" class="w-1 h-1 rounded-full bg-black absolute translate-y-[35px]" :class="theme === 'customLightTheme' ? 'bg-black' : 'bg-white'" />
        </div>

        <!-- Trash empty -->
        <div v-if="deletedFolders?.length" class="flex flex-col items-center justify-center relative">
          <v-img :src="trashFull" :aspect-ratio="1" :width="58" class="mb-1" />

          <div v-if="trashActive" class="w-1 h-1 rounded-full absolute translate-y-[35px]" :class="theme === 'customLightTheme' ? 'bg-black' : 'bg-white'" />
        </div>

        <!-- Trash full -->
        <div v-else class="flex flex-col items-center justify-center relative">
          <v-img :src="trash" :aspect-ratio="1" :width="58" class="mb-1" />

          <div v-if="trashActive" class="w-1 h-1 rounded-full absolute translate-y-[35px]" :class="theme === 'customLightTheme' ? 'bg-black' : 'bg-white'" />
        </div>
      </div>
    </template>
  </v-hover>
</template>

<script setup>
import { ref } from 'vue';
import { useTheme } from 'vuetify';
import finder from '@/assets/finder.png'
import safari from '@/assets/safari.png'
import store from '@/assets/app-store.png'
import messages from '@/assets/messages.png'
import maps from '@/assets/maps.png'
import contacts from '@/assets/contacts.png'
import mail from '@/assets/mail.png'
import reminders from '@/assets/reminders.png'
import notes from '@/assets/notes.png'
import settings from '@/assets/settings.png'
import trash from '@/assets/trash.png'
import trashFull from '@/assets/trash_full.png'
import { storeToRefs } from 'pinia';
import { useGeneralStore } from '../stores/general.store';

const { deletedFolders } = storeToRefs(useGeneralStore())

const theme = useTheme().name

const trashActive = ref(false)
const images = ref([
  {
    id: 'finder',
    logo: finder,
    width: 62,
    active: true,
  },
  {
    id: 'safari',
    logo: safari,
    width: 53,
    active: false,
  },
  {
    id: 'store',
    logo: store,
    width: 56,
    active: false,
  },
  {
    id: 'messages',
    logo: messages,
    width: 52,
    active: false,
  },
  {
    id: 'maps',
    logo: maps,
    width: 62,
    active: false,
  },
  {
    id: 'contacts',
    logo: contacts,
    width: 58,
    active: false,
  },
  {
    id: 'mail',
    logo: mail,
    width: 65,
    active: false,
  },
  {
    id: 'reminders',
    logo: reminders,
    width: 54,
    active: false,
  },
  {
    id: 'notes',
    logo: notes,
    width: 63,
    active: false,
  },
  {
    id: 'settings',
    logo: settings,
    width: 63,
    active: false,
  },
])
</script>