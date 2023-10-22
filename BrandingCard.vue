<script setup lang="ts">
import { ref, computed } from 'vue'
import SwitchUI from '@/components/applets/SwitchUI.vue'
import IconLogo from '@/components/icons/iconLogo.vue'

interface Props {
  companyName: string
  termsOfService: string
  privacyPolicy: string
  useTermsPrivacy: boolean
}

const props = defineProps<Props>()

const emit = defineEmits([
  'update:companyName',
  'update:termsOfService',
  'update:privacyPolicy',
  'update:useTermsPrivacy'
])

const companyNameChanged = computed({
  get() {
    return props.companyName
  },
  set(value) {
    emit('update:companyName', value)
  }
})

const termsOfServiceChanged = computed({
  get() {
    return props.termsOfService
  },
  set(value) {
    emit('update:termsOfService', value)
  }
})

const privacyPolicyChanged = computed({
  get() {
    return props.privacyPolicy
  },
  set(value) {
    emit('update:privacyPolicy', value)
  }
})

const currentAccentColor = ref('')
</script>

<template>
  <div class="card">
    <div class="titleBlock">
      <h3 class="title startPage">Start Page</h3>
      <span
        >Customize branding and company information that will appear on the
        start page of all of your workflows</span
      >
    </div>
    <div class="upload">
      <div>
        <h3 class="title">Logo</h3>
        <span>Examples: .PNG, .JPG, .SVG</span>
      </div>
      <div class="imageBlock">
        <IconLogo />
        <img class="deleteIcon" src="@/assets/clear-photo.svg" alt="del" />
      </div>
    </div>
    <div class="accentColor">
      <h3 class="title">Accent Color</h3>
      <div class="accentColorBlock">
        <div class="colorPreview" />
        <input
          v-model="currentAccentColor"
          type="text"
          maxlength="7"
          class="input"
        />
        <img
          class="deleteIcon"
          src="@/assets/clear-color.svg"
          alt="del"
          @click="currentAccentColor = '#ffffff'"
        />
      </div>
    </div>
    <div class="titleBlock">
      <h3 class="title">Company Display Name</h3>
      <input
        v-model="companyNameChanged"
        type="text"
        class="input-square"
        placeholder="Enter Name"
      />
    </div>
    <div class="titleBlock">
      <h3 class="title">Terms of Service</h3>
      <input
        v-model="termsOfServiceChanged"
        type="text"
        class="input-square"
        placeholder="Enter URL"
      />
    </div>
    <div class="titleBlock">
      <h3 class="title">Privacy Policy</h3>
      <input
        v-model="privacyPolicyChanged"
        type="text"
        class="input-square"
        placeholder="Enter URL"
      />
    </div>
    <div class="switchBlock">
      <SwitchUI :value="useTermsPrivacy" tooltip-text="" />
      <span class="title">Use Vyyer’s Terms & Privacy</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  padding: 0 24px;
  .upload {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 24px 0;
    border-bottom: 1px solid #eceef1;
    div {
      .title {
        padding-bottom: 5px;
      }
      span {
        font-family: 'Inter';
        font-size: 13px;
        font-weight: normal;
        line-height: 1.54;
        letter-spacing: normal;
        color: var(--2-secondary-secondary-500);
      }
    }
    .imageBlock {
      position: relative;
      &:hover .deleteIcon {
        display: block;
      }
      .deleteIcon {
        display: none;
        position: absolute;
        top: -4px;
        right: -11px;
      }
    }
  }
  .switchBlock {
    padding: 24px 0;
    display: flex;
    align-items: center;
    gap: 12px;
    .title {
      padding-bottom: 0px;
    }
  }
  .input-square {
    width: 100%;
  }
  .titleBlock {
    padding: 24px 0;
    position: relative;
    border-bottom: 1px solid var(--7-gray-gray-100);
    span {
      font-family: 'Inter';
      font-size: 15px;
      font-weight: normal;
      line-height: 1.54;
      letter-spacing: normal;
      color: var(--2-secondary-secondary-500);
    }
  }
  .accentColor {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    border-bottom: 1px solid var(--7-gray-gray-100);
    padding: 32px 0;
    .title {
      padding-bottom: 0px;
    }
    .accentColorBlock {
      display: flex;
      width: 132px;
      height: 38px;
      border: 1px solid var(--7-gray-gray-200);
      border-radius: 6px;
      position: relative;
      .colorPreview {
        width: 38px;
        border-right: 1px solid var(--7-gray-gray-200);
        background-color: v-bind(currentAccentColor);
        border-radius: 6px 0 0 6px;
      }
      .input {
        width: 94px;
        padding: 7px 12px;
        border: none;
        border-radius: 0 6px 6px 0;
        font-size: 15px;
        font-weight: normal;
        line-height: 1.53;
        text-transform: uppercase;
        &:focus {
          border: none;
          outline: none;
          box-shadow: unset;
        }
      }
      &:hover {
        .deleteIcon {
          display: block;
        }
      }
      .deleteIcon {
        display: none;
        position: absolute;
        top: -4px;
        right: -11px;
        cursor: pointer;
      }
    }
  }
  .title {
    font-family: 'Inter';
    font-size: 15px;
    font-weight: 500;
    line-height: 1.53;
    letter-spacing: normal;
    color: var(--label-1-primary);
    padding-bottom: 12px;
  }
  .startPage {
    font-weight: 600;
  }
}
</style>
