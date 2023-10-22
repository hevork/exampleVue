<script setup lang="ts">
import IconLogo from '@/components/icons/iconLogo.vue'
import IconId from '@/components/icons/iconId.vue'
import IconClock from '@/components/icons/iconClock.vue'
const props = defineProps({
  termsOfService: {
    type: String,
    default: ''
  },
  privacyPolicy: {
    type: String,
    default: ''
  }
})
</script>

<template>
  <div class="previewBlock">
    <h3>Preview</h3>
    <div class="preview">
      <img class="statusBar" src="@/assets/bars-status.svg" alt="bars-status" />
      <div class="body">
        <div class="delete">
          <img class="deleteIcon" src="@/assets/clear-preview.svg" alt="del" />
        </div>
        <div class="content">
          <IconLogo />
          <h1>Vyyer wants to verify your identity</h1>
          <span>What will I need for verification?</span>
          <div class="infoCard">
            <IconId />A state ID Card or Driver’s License
          </div>
          <div class="infoCard">
            <IconClock />A state ID Card or Driver’s License
          </div>
        </div>
        <div class="button">
          <span>Start</span>
          <div>
            <a :href="props.termsOfService">Terms</a>
            <a :href="props.privacyPolicy">Privacy</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.previewBlock {
  display: flex;
  flex-direction: column;
  margin: 24px 24px 67px 24px;
  padding: 87px 0 135px 0;
  width: 65%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 10px;
  border: solid 1px var(--7-gray-gray-100);
  background-color: #f9fafb;
  @media screen and (max-width: 1150px) {
    width: auto;
    height: 100%;
    padding: auto 0;
    margin: 0px;
    border-radius: 0px;
  }
  @media screen and (max-width: 900px) {
    padding: 40px 0;
  }
  h3 {
    font-family: 'Inter';
    font-size: 15px;
    font-weight: normal;
    line-height: 1.53;
    letter-spacing: normal;
    color: var(--7-gray-gray-800);
    margin-bottom: 24px;
  }
  .preview {
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
    height: 500px;
    .statusBar {
      background-color: black;
    }
    .body {
      background-image: linear-gradient(
        to bottom,
        var(--label-1-primary),
        #434343
      );
      display: flex;
      align-items: center;
      flex-direction: column;
      justify-content: space-between;
      flex: 1 1 auto;
      .content {
        display: flex;
        align-items: center;
        flex-direction: column;
        h1 {
          font-family: 'Inter';
          font-size: 14.8px;
          font-weight: 600;
          line-height: 1.25;
          letter-spacing: 0.21px;
          text-align: center;
          color: #ffffff;
          margin-top: 20px;
          overflow: hidden;
          max-width: 200px;
          max-height: 50px;
        }
        span {
          font-family: 'Inter';
          font-size: 9.9px;
          font-weight: normal;
          line-height: 1.5;
          letter-spacing: normal;
          text-align: center;
          color: #eceef1;
          padding: 0 15px;
          margin-top: 10px;
          overflow: hidden;
          max-width: 200px;
          max-height: 50px;
        }
        .infoCard {
          padding: 10px 11px 9px;
          border-radius: 6.2px;
          margin: 15px 15px 0 15px;
          border: solid 0.7px rgba(198, 198, 200, 0.3);
          font-family: 'Inter';
          font-size: 9.9px;
          font-weight: normal;
          line-height: 1.5;
          letter-spacing: normal;
          text-align: center;
          color: #ffffff;
          display: flex;
          align-items: center;
          justify-content: center;
          gap: 6px;
        }
      }
      .delete {
        width: 100%;
        .deleteIcon {
          display: flex;
          margin: 22px 0 0 10px;
          cursor: pointer;
        }
      }
      .button {
        display: flex;
        flex-direction: column;
        width: 100%;
        padding: 0 15px;
        span {
          display: flex;
          align-items: center;
          justify-content: center;
          width: 100%;
          border-radius: 6.2px;
          margin-bottom: 14px;
          padding: 9.5px 0 8.5px 0;
          background-color: #ffffff;
          font-family: 'Inter';
          font-size: 9.9px;
          font-weight: 600;
          line-height: 1.25;
          letter-spacing: 0.31px;
          color: var(--label-1-primary);
          cursor: pointer;
        }
        div {
          display: flex;
          align-items: center;
          justify-content: center;
          gap: 10px;
          width: 100%;
          margin-bottom: 28px;
          font-family: 'Inter';
          font-size: 8px;
          font-weight: 600;
          line-height: 1.54;
          letter-spacing: normal;
          color: rgba(235, 235, 245, 0.6);
          text-decoration: underline;
          cursor: pointer;
        }
      }
    }
  }
}
</style>
