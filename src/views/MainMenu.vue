<template>
  <div class="difficulty-container">
    <h1>WTFlags</h1>
    <div class="select-container">
      <ion-select :label="$t('difficulty')" v-model="difficulty" aria-label="{{$t('choose_difficulty')}}"
                  interface="popover"
                  @ionChange="changeDifficulty" label-placement="floating">
        <ion-select-option value="0">
          {{ $t('easy') }}
        </ion-select-option>
        <ion-select-option value="1">
          {{ $t('medium') }}
        </ion-select-option>
        <ion-select-option value="2">
          {{ $t('hard') }}
        </ion-select-option>
        <ion-select-option value="3">
          {{ $t('very_hard') }}
        </ion-select-option>
      </ion-select>
    </div>
    <div class="start-container">
    <ion-button color="primary" expand="block" @click="$router.push('/Game')">{{ $t('start') }}</ion-button>
    </div>
    <footer class="container-flags">
      <button v-for="(lang, i) in langs" :key="i" @click="changeLanguage($i18n, lang.code)">
        <img
            :alt="lang.name"
            :src="`https://flagcdn.com/24x18/${lang.flag}.png`"
            height="18"
            width="24">
      </button>
    </footer>
  </div>
</template>

<script lang="ts" setup>
import {IonButton, IonSelect, IonSelectOption} from '@ionic/vue';
import {ExportedGlobalComposer} from "vue-i18n";
import {ref} from "vue";

const difficulty = ref(localStorage.getItem('difficulty') || '0');
const langs: any[] = [
  {code: 'en', flag: 'gb', name: 'English'},
  {code: 'es', flag: 'es', name: 'Spanish'},
  {code: 'kr', flag: 'kr', name: 'Korean'}
];

function changeDifficulty() {
  console.log(difficulty.value)
  localStorage.setItem('difficulty', difficulty.value);
}

function changeLanguage(i18n: ExportedGlobalComposer, langCode: string) {
  i18n.locale = langCode;
  localStorage.setItem('locale', langCode);
}
</script>

<style scoped>
.difficulty-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  margin-top: 15vh;
}

.select-container, .start-container {
  width: clamp(300px, 50%, 600px);
}

ion-button {
  text-transform: none;
}

h1 {
  font-size: 5em;
  margin-bottom: 30px;
  user-select: none;
  text-shadow: 3px 0 #f44336, -3px 0 #00e5e5, 0 3px #e0ac08, 0 -3px #2dd36f,
  2px 2px #f44336, -2px -2px #00e5e5, 2px -2px #e0ac08, -2px 2px #2dd36f;
}

.container-flags {
  position: absolute;
  bottom: 5px;
  display: flex;
  gap: .25em;
}

.container-flags button {
  width: unset;
  background: none;
}
</style>
