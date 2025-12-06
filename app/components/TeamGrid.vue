<template>
  <div class="px-0 mb-5">
    <div class="grid xl:grid-cols-5 lg:grid-cols-3 md:grid-cols-3 sm:grid-cols-2 gap-x-6 gap-y-6">
      <div
        v-for="(member, idx) in teamMembers" :key="idx"
        class="
          bg-red-900 dark:bg-gray-900 border border-red-700 dark:border-gray-300 rounded-xl p-3
          flex flex-row items-center
          sm:flex-col sm:items-center sm:text-center
          transition-colors duration-200
        "
      >
        <!-- Left: profile image -->
        <div class="w-20 h-20  lg:w-36 lg:h-36 rounded-full border-2 border-white dark:border-gray-500 bg-red-50 dark:bg-gray-800 overflow-hidden flex-shrink-0 transition-colors duration-200">
          <NuxtImg :src="member.img"
                   sizes="100vw sm:50vw md:400px"
                   :alt="`${member.name} Profile`" />
        </div>

        <!-- Right/Below: info + links -->
        <div class="flex-grow flex flex-col justify-center sm:justify-center sm:mt-4">
          <div class="flex flex-col justify-center items-center text-center sm:items-center sm:text-center px-2">
            <h4 class="text-red-50 dark:text-gray-100 text-base font-semibold transition-colors duration-200">{{ member.name }}</h4>
            <p class="text-orange-200 dark:text-gray-400 text-[13px] mt-1 transition-colors duration-200">{{ member.role }}</p>
          </div>
          <div class="space-x-4 mt-4 flex justify-center items-center">
            <a :href="member.telegramLink || '#'"
               target="_blank" rel="noopener"
               class="w-7 h-7 inline-flex items-center justify-center rounded-full hover:bg-red-100 dark:hover:bg-gray-800 group transition-colors duration-200">
              <Icon name="i-stash-telegram" class="w-5 h-5 text-stone-200 dark:text-gray-400 group-hover:text-red-600 dark:group-hover:text-yellow-400 transition-colors duration-200" />

            </a>
            <a :href="member.emailLink ? `mailto:${member.emailLink}` : '#'"
               class="w-7 h-7 inline-flex items-center justify-center rounded-full hover:bg-red-100 dark:hover:bg-gray-800 group transition-colors duration-200">
              <Icon name="i-lucide-mail" class="w-5 h-5 text-stone-200 dark:text-gray-400 group-hover:text-red-600 dark:group-hover:text-yellow-400 transition-colors duration-200" />
            </a>
            <button @click="openDetails(member)"
                    class="w-7 h-7 inline-flex items-center justify-center rounded-full hover:bg-red-100 dark:hover:bg-gray-800 group transition-colors duration-200 cursor-pointer">
              <Icon name="i-lucide-info" class="w-5 h-5 text-stone-200 dark:text-gray-400 group-hover:text-red-600 dark:group-hover:text-yellow-400 transition-colors duration-200" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <UModal v-model:open="showModal" :title="activeMember?.name"
        :description="activeMember?.role"
        :ui="{
          base: 'relative text-left rtl:text-right overflow-hidden my-24 mx-4',
          background: 'bg-white dark:bg-gray-900',
          rounded: 'rounded-lg',
          shadow: 'shadow-xl',
          width: 'max-w-lg',
          padding: 'p-6'
        }"
        :close="{
          color: 'gray',
          variant: 'ghost',
          size: 'sm',
          icon: 'i-heroicons-x-mark-20-solid',
          class: 'absolute top-4 right-4 text-gray-400 hover:text-gray-700 dark:text-gray-400 dark:hover:text-gray-200'
        }"
>
  <template #header>
    <div>
      <div class="flex-1 mt-2">
        <h3 class="text-xl font-bold text-gray-800 dark:text-gray-100">{{ activeMember?.name }}</h3>
        <p class="text-blue-500 dark:text-yellow-400 font-medium text-sm mt-2">{{ activeMember?.role }}</p>
      </div>
    </div>
  </template>
  
  <template #body>
    <div class="space-y-4">
      <!-- Email -->
      <div class="group">
        <div class="flex items-center gap-4 p-4 rounded-lg border border-gray-200 dark:border-gray-700 hover:border-blue-300 dark:hover:border-yellow-500 hover:bg-blue-50/50 dark:hover:bg-gray-800 transition-all duration-200">
          <div class="w-10 h-10  rounded-lg bg-blue-100 dark:bg-gray-800 flex items-center justify-center">
            <UIcon name="i-lucide-mail" class="size-5 text-blue-600 dark:text-blue-400" />
          </div>
          <div class="flex-1 min-w-0">
            <span class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wider">Email</span>
            <a 
              :href="`mailto:${activeMember?.email}`"
              class="block text-gray-800 dark:text-gray-100 font-medium truncate hover:text-blue-600 dark:hover:text-blue-300 transition-colors duration-200 mt-0.5"
            >
              {{ activeMember?.email }}
            </a>
          </div>
          <UIcon name="i-lucide-external-link" class="size-4 text-gray-400 dark:text-gray-500 hover:text-blue-500 dark:hover:text-yellow-500 transition-colors duration-200" />
        </div>
      </div>

      <!-- Extension -->
      <div class="group">
        <div class="flex items-center gap-4 p-4 rounded-lg border border-gray-200 dark:border-gray-700 hover:border-green-300 dark:hover:border-yellow-500 hover:bg-green-50/50 dark:hover:bg-gray-800 transition-all duration-200">
          <div class="w-10 h-10 rounded-lg bg-green-100 dark:bg-gray-800 flex items-center justify-center">
            <UIcon name="i-lucide-phone" class="size-5 text-green-600 dark:text-green-400" />
          </div>
          <div class="flex-1 min-w-0">
            <span class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wider">Extension</span>
            <p class="text-gray-800 dark:text-gray-100 font-medium mt-0.5">
              {{ activeMember?.ext || '—' }}
            </p>
          </div>
          <UIcon name="i-lucide-copy" class="size-4 text-gray-400 dark:text-gray-500 hover:text-green-500 dark:hover:text-yellow-500 transition-colors duration-200 cursor-pointer" 
                 @click="copyToClipboard(activeMember?.ext)" />
        </div>
      </div>

      <!-- Phone -->
      <div class="group">
        <div class="flex items-center gap-4 p-4 rounded-lg border border-gray-200 dark:border-gray-700 hover:border-purple-300 dark:hover:border-yellow-500 hover:bg-purple-50/50 dark:hover:bg-gray-800 transition-all duration-200">
          <div class="w-10 h-10 rounded-lg bg-purple-100 dark:bg-gray-800 flex items-center justify-center">
            <UIcon name="i-lucide-smartphone" class="size-5 text-purple-600 dark:text-gray-400" />
          </div>
          <div class="flex-1 min-w-0">
            <span class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wider">Mobile Phone</span>
            <p class="text-gray-800 dark:text-gray-100 font-medium mt-0.5">
              {{ activeMember?.phone || '—' }}
            </p>
          </div>
          <UIcon name="i-lucide-copy" class="size-4 text-gray-400 dark:text-gray-500 hover:text-purple-500 dark:hover:text-yellow-500 transition-colors duration-200 cursor-pointer"
                 @click="copyToClipboard(activeMember?.phone)" />
        </div>
      </div>
    </div>
  </template>
  </UModal>

</template>


<script setup>
import { ref } from 'vue'
const teamMembers = [
  {
    name: 'Huy Chantha',
    role: 'Manager, System Engineering',
    img: 'images/chantha-huy.jpg',
    email: 'chantha.huy@canadiabank.com.kh',
    phone: '098966898',
    ext: '77862',
    telegramLink: 'https://t.me/chantha_huy',
    emailLink: 'chantha.huy@canadiabank.com.kh',
  },
  {
    name: 'Nhim Monica',
    role: 'Senior Officer, System Engineering',
    img: 'images/monica-nhim.jpg',
    email: 'monica.nhim@canadiabank.com.kh',
    phone: '-',
    ext: '77943',
    telegramLink: 'https://t.me/Monica_Nhim',
    emailLink: 'monica.nhim@canadiabank.com.kh',
  },
  {
    name: 'Reth Soklin',
    role: 'Senior Officer, System Engineering',
    img: 'images/soklin-reth.jpg',
    email: 'soklin.reth@canadiabank.com.kh',
    phone: '0965967711',
    ext: '-',
    telegramLink: 'https://t.me/soklinreth',
    emailLink: 'soklin.reth@canadiabank.com.kh',
  },
  {
    name: 'Nat Karona',
    role: 'Senior Officer, System Engineering',
    img: 'images/karona.png',
    email: 'karona.nat@canadiabank.com.kh',
    phone: '081829569',
    ext: '-',
    telegramLink: 'https://t.me/karona_nat',
    emailLink: 'karona.nat@canadiabank.com.kh',
  },
  {
    name: 'Sok Elodie',
    role: 'Officer, System Engineering',
    img: 'images/elodie-sok.jpg',
    email: 'elodie.sok@canadiabank.com.kh',
    phone: '0963656212',
    ext: '78196',
    telegramLink: 'https://t.me/msslody',
    emailLink: 'elodie.sok@canadiabank.com.kh',
  },
];

const showModal = ref(false)
const activeMember = ref(null)

function openDetails(member) {
  activeMember.value = member
  showModal.value = true
}
</script>
