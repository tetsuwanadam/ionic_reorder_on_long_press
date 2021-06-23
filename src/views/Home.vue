<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Ionic Reorder on Long Press</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Ionic Reorder on Long Press</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <ion-list>
        <ion-reorder-group @ionItemReorder="reorder($event)" :disabled="reorderIsDisabled">
          <ion-item-sliding>
            <ion-item-options side="start">
              <ion-item-option>Button</ion-item-option>
            </ion-item-options>

            <ion-item>
              <ion-reorder slot="start"></ion-reorder>
              <ion-label>Item 1</ion-label>
            </ion-item>
          </ion-item-sliding>

          <ion-item-sliding>
            <ion-item-options side="start">
              <ion-item-option>Button</ion-item-option>
            </ion-item-options>

            <ion-reorder>
              <ion-item>
                <ion-label>Item 2</ion-label>
              </ion-item>
            </ion-reorder>
          </ion-item-sliding>

          <ion-item-sliding>
            <ion-item-options side="start">
              <ion-item-option>Button</ion-item-option>
            </ion-item-options>

            <ion-item>
              <ion-reorder slot="start"></ion-reorder>
              <ion-label>Item 3</ion-label>
            </ion-item>
          </ion-item-sliding>
        </ion-reorder-group>
      </ion-list>

      <p>
        <ion-button @click="reorderIsDisabled = !reorderIsDisabled" size="small">Toggle</ion-button>
        Reorder is {{ (reorderIsDisabled) ? 'disabled' : 'enabled' }}
      </p>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonButton, IonContent, IonHeader, IonItem, IonItemSliding, IonPage, IonReorder, IonReorderGroup, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonButton,
    IonContent,
    IonHeader,
    IonItem,
    IonItemSliding,
    IonPage,
    IonReorder,
    IonReorderGroup,
    IonTitle,
    IonToolbar,
  },
  setup: function() {
    const reorder = function(event) {
      console.log('reorder event is:', event);
      event.detail.complete();
    };

    const reorderIsDisabled = ref(false);

    return {
      reorder,
      reorderIsDisabled,
    };
  },
});
</script>

<style scoped>

</style>