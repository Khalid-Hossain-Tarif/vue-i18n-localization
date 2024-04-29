<script setup>
import { RouterLink, RouterView } from 'vue-router'

const changeLocale = () => {
  if (locale == 'ar') {
    document.querySelector('body').classList.toggle('rtl');
    console.log('ar')
  }
}
</script>

<template>
  <header class="bg-red-50 px-20 py-5 flex justify-between" :dir="$i18n.locale == 'ar' ? 'rtl' : 'ltr'">
    <nav class="flex items-center">
      <router-link to="/" class="px-5 font-medium">{{ $t('Home') }}</router-link>
      <router-link to="/about" class="px-5 font-medium">{{ $t('About') }}</router-link>
    </nav>

    <div>
      <select v-model="$i18n.locale" @change="changeLocale">
        <option v-for="locale in $i18n.availableLocales" :key="`locale-${locale}`" :value="locale">{{ locale }}</option>
      </select>
    </div>
  </header>

  <RouterView />
</template>