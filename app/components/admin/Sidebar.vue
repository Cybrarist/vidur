<script setup lang="ts">
const { data: careerSiteConfig } = useCareerSiteConfigObjectState();
const logoURL = computed(() => useRemoteAsset(careerSiteConfig.value.logo).url);

const publicConfig = useRuntimeConfig().public;
</script>

<template>
  <div class="flex fixed top-0 left-0 flex-col px-4 py-6 md:border-r border-zinc-200 h-screen">
    <div class="flex flex-col">
      <!-- Company Profile -->
      <div class="flex items-center">
        <img class="rounded-lg w-8 border border-zinc-200" :src="logoURL" alt="avatar" />
        <span class="font-semibold ml-2 truncate font-noto overflow-hidden">
          {{ careerSiteConfig.name }}
        </span>
      </div>
      <div class="text-xs text-zinc-500 mb-2 mt-6">Menu</div>
      <ul class="flex flex-nowrap md:block mr-3 md:mr-0">
        <AdminSidebarLink to="/admin/dashboard" icon="iconoir:home-simple" label="Home" />
        <AdminSidebarLink to="/admin/applications" icon="iconoir:user-badge-check" label="Applications" />
        <AdminSidebarLink to="/admin/integrations" icon="hugeicons:connect" label="Integrations" />
        <AdminSidebarLink to="/admin/settings" icon="iconoir:settings" label="Settings" />
      </ul>
    </div>

    <!-- Discord -->
    <div class="mt-auto">
      <!-- <div class="p-2 border border-zinc-200 rounded-xl">
        <div class="flex items-center space-x-2">
          <img src="/vidur-logo.svg" class="w-14" />
          <div
            class="py-1 px-2 text-xs border border-amber-300 rounded-lg bg-amber-50 text-amber-500 font-medium"
          >
            premium
          </div>
        </div>
        <div class="text-xs my-2 text-zinc-500">
          Get access to AI powered profiles and People's Search.
        </div>
        <VInputButton size="sm">Upgrade Now</VInputButton>
      </div> -->
      <div class="flex justify-between mt-4">
        <div class="text-zinc-900 text-sm">{{ publicConfig.version }}</div>
        <div class="flex space-x-2 items-center text-zinc-900">
          <a :href="publicConfig.github" target="_blank">
            <Icon class="w-5 h-5 shrink-0 fill-current" name="mdi:github" />
          </a>
          <a :href="publicConfig.discord" target="_blank">
            <Icon class="w-5 h-5 shrink-0 fill-current" name="ic:sharp-discord" />
          </a>
          <a :href="publicConfig.twitter" target="_blank">
            <Icon class="w-4 h-4 shrink-0 fill-current" name="pajamas:twitter" />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
