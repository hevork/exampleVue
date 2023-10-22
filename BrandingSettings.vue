<script setup lang="ts">
import { ref } from 'vue'
import BreadcrumbsUI from '@/components/applets/BreadcrumbsUI.vue'
import { ROUTES } from '@/router/routes'
import BrandingCard from '@/components/settings/BrandingCard.vue'
import BrandingPreview from '@/components/settings/BrandingPreview.vue'

const formMessage = ref({
  companyName: 'Vyyer Technologies',
  termsOfService: 'https://website.com/termsofservice',
  privacyPolicy: 'https://website.com/privacypolicy',
  useTermsPrivacy: false
})

const breadcrumbs = [
  { routeName: ROUTES.SETTINGS.SETTINGS_INDEX, text: 'Settings' },
  { routeName: ROUTES.SETTINGS.BRANDING, text: 'Branding' }
]
</script>

<template>
  <section>
    <BreadcrumbsUI :breadcrumbs="breadcrumbs" />

    <div class="wrapper">
      <div class="titleBlock">
        <h1>Branding</h1>
        <div class="buttons">
          <button class="btn-active">Save Changes</button>
        </div>
      </div>
      <div class="contentBody">
        <div class="settings">
          <div class="form">
            <BrandingCard
              v-model:company-name="formMessage.companyName"
              v-model:privacy-policy="formMessage.privacyPolicy"
              v-model:terms-of-service="formMessage.termsOfService"
              v-model:use-terms-privacy="formMessage.useTermsPrivacy"
            />
          </div>
        </div>
        <div>
          <BrandingPreview
            :privacy-policy="formMessage.privacyPolicy"
            :terms-of-service="formMessage.termsOfService"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
section {
  padding-bottom: 60px;

  .wrapper {
    border: 1px solid #eceef1;
    border-radius: 10px;
    .titleBlock {
      display: flex;
      justify-content: space-between;
      padding: 20px 24px;
      flex-wrap: wrap;
      h1 {
        font-family: 'Inter';
        font-size: 22px;
        font-weight: 600;
        line-height: 1.41;
        color: var(--label-1-primary);
      }
      .buttons {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
      }
    }
    .contentBody {
      border-top: solid 1px var(--7-gray-gray-100);
      border-bottom: solid 1px var(--7-gray-gray-100);
      display: grid;
      grid-template-columns: 400px auto;
      @media screen and (max-width: 900px) {
        grid-template-columns: auto;
      }
      .settings {
        border-right: solid 1px var(--7-gray-gray-100);
        @media screen and (max-width: 900px) {
          border-right: none;
        }
      }
    }
  }
}
</style>
