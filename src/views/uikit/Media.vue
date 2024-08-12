<script setup>
import { ref, onMounted } from 'vue';
import {VocabularyServices} from '@/service/VocabularyServices';
const vocabularies = ref([])
const play = () => {
  audioElement.play()
};

const audioElement = new Audio("/audio/new_audio.mp3");

const products = ref([]);
const images = ref([]);
const galleriaResponsiveOptions = ref([
    {
        breakpoint: '1024px',
        numVisible: 5
    },
    {
        breakpoint: '960px',
        numVisible: 4
    },
    {
        breakpoint: '768px',
        numVisible: 3
    },
    {
        breakpoint: '560px',
        numVisible: 1
    }
]);
const carouselResponsiveOptions = ref([
    {
        breakpoint: '1024px',
        numVisible: 1,
        numScroll: 1
    },
    {
        breakpoint: '768px',
        numVisible: 1,
        numScroll: 1
    },
    {
        breakpoint: '560px',
        numVisible: 1,
        numScroll: 1
    }
]);
const vocabularyServices = new VocabularyServices();


onMounted(() => {
  vocabularyServices.getVocabularies().then((data) => (vocabularies.value = data))
    // productService.getProductsSmall().then((data) => (products.value = data));
    // photoService.getImages().then((data) => (images.value = data));
});

const getSeverity = (status) => {
    switch (status) {
        case 'INSTOCK':
            return 'success';

        case 'LOWSTOCK':
            return 'warning';

        case 'OUTOFSTOCK':
            return 'danger';

        default:
            return null;
    }
};
const breadcrumbItems = ref([{ label: 'Computer' }, { label: 'Notebook' }, { label: 'Accessories' }, { label: 'Backpacks' }, { label: 'Item' }]);

</script>

<template>

<!--  <div class="relative">-->
<!--    <div class="static bg-primary-100 p-4 border-round text-gray-800" style="min-width: 300px; min-height: 150px;">-->
<!--      <p class="font-bold text-gray-900">Static</p>-->
<!--      <div class="absolute bottom-5 left-5 bg-primary border-round p-4 font-bold " style="min-width: 120px; min-height: 70px">-->
<!--        Absolute-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->

  <!--  <div class="flex align-items-center justify-content-start">-->
<!--    <div class="w-4rem h-4rem bg-primary font-bold p-4 border-round mr-3">1</div>-->
<!--    <div class="w-4rem h-4rem bg-primary font-bold flex align-items-center justify-content-center p-4 border-round mr-3">21</div>-->
<!--    <div class="w-4rem h-4rem bg-primary font-bold flex align-items-center justify-content-center p-4 border-round">3</div>-->
<!--  </div>-->

<!--  <div class="block bg-primary font-bold text-center p-4 border-round mb-3">1</div>-->
<!--  <div class="block bg-primary font-bold text-center p-4 border-round mb-3">2</div>-->
<!--  <div class="block bg-primary font-bold text-center p-4 border-round mb-3">3</div>-->

<!--  <div class="inline bg-primary font-bold text-center p-4 border-round mx-4">1</div>-->
<!--  <div class="inline bg-primary font-bold text-center p-4 border-round mx-4">2</div>-->
<!--  <div class="inline bg-primary font-bold text-center p-4 border-round mx-4">3</div>-->

<!--  <div class="flex">-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round">1</div>-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round mx-4">2</div>-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round">3</div>-->
<!--  </div>-->

<!--  <div class="inline-flex">-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round">1</div>-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round mx-4">2</div>-->
<!--    <div class="flex-1 h-4rem bg-primary font-bold text-center p-4 border-round">3</div>-->
<!--  </div>-->

<!--  <div class="inline-flex">-->
<!--    <div class="hidden md:block bg-primary font-bold align-items-center justify-content-center p-4 border-round mr-3">Visible on a middle or larger screen</div>-->
<!--    <div class="block md:hidden bg-primary font-bold align-items-center justify-content-center p-4 border-round mr-3">Visible on a small screen</div>-->
<!--  </div>-->

<!--  <div class="line-height-3">-->
<!--    <div class="overflow-hidden  surface-overlay p-3 border-primary-500 border-2 border-round" style="height: 100px">-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit-->
<!--      esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,-->
<!--      quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.-->
<!--      quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit-->
<!--      esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,-->
<!--      quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.-->
<!--      quis-->
<!--    </div>-->
<!--  </div>-->

<!--  <div class="line-height-3">-->
<!--    <div class="overflow-hidden md:overflow-auto surface-overlay p-3 border-primary-500 border-2 border-round" style="height: 100px">-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--      Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit-->
<!--      esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.-->
<!--      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,-->
<!--      quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.-->
<!--    </div>-->
<!--  </div>-->


  <!--  <div class="grid">-->
<!--    <div class="col-12">-->
<!--      <div class="card">-->
<!--        <div class="flex justify-content-center">-->
<!--          <Image  :src="'/images/generated_picture_0.png'" alt="Image" />-->
<!--        </div>-->
<!--        <div class="flex justify-content-center" >-->
<!--          <Button type="button" class="mr-2 mb-2" label="Search" icon="pi pi-search"  />-->
<!--          <Button type="button" class="mr-2 mb-2" label="Search" icon="pi pi-search" />-->
<!--          <Button type="button" class="mr-2 mb-2" icon="pi pi-search" />-->
<!--          <Button type="button" class="mr-2 mb-2" label="Search" />-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->
<!--  </div>-->

  <div class="col-12">
      <div class="flex align-items-center justify-content-center font-bold border-round m-2">
        <Breadcrumb :home="breadcrumbHome" :model="breadcrumbItems" />
      </div>
      <div class="flex align-items-center justify-content-center">
        <div class="flex align-items-center justify-content-center font-bold border-round m-2">
          <Button icon="pi pi-arrow-left" severity="info" rounded outlined class="mb-3 mr-3" />
        </div>
        <div class="flex flex-column font-bold border-round m-2">
          <div class="flex align-items-center justify-content-center font-bold border-round m-2">
            <Image :src="'/images/vocabulary/soccer.jpg'" alt="Image" height="350px" />
          </div>
          <div class="flex align-items-center justify-content-center mb-3 font-bold" >
            <h3><span class="first">book &nbsp;</span></h3>
            <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />
          </div>
          <div class="flex align-items-center justify-content-center mb-3 font-bold">
            <h3><span>下午</span></h3>
          </div>
          <div class="flex align-items-center justify-content-center mb-3 font-bold">
            <h4>漂亮</h4> &nbsp;&nbsp;
            <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />
          </div>
        </div>
        <div class="flex align-items-center justify-content-center font-bold border-round m-2">
          <Button icon="pi pi-arrow-right " severity="info" rounded outlined class="mb-3 mr-3" />
        </div>
      </div>
    </div>


<!--  <div class="col-12">-->
<!--    <div class="card">-->
<!--      <div class="flex justify-content-center">-->
<!--        <Image :src="'/images/vocabulary/soccer.jpg'" alt="Image" width="784" />-->
<!--      </div>-->
<!--      <div class="flex align-items-center justify-content-center mb-3 font-bold" >-->
<!--        <h3><span class="first">book &nbsp;</span></h3>-->
<!--        <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--      </div>-->
<!--      <div class="flex align-items-center justify-content-center mb-3 font-bold">-->
<!--        <h3><span>下午</span></h3>-->
<!--      </div>-->
<!--      <div class="flex align-items-center justify-content-center mb-3 font-bold">-->
<!--        <h4>漂亮</h4> &nbsp;&nbsp;-->
<!--        <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--      </div>-->

<!--      <Toolbar class="mb-3">-->
<!--        <template v-slot:start>-->
<!--          <div class="my-2">-->
<!--            <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--          </div>-->
<!--        </template>-->
<!--        <template v-slot:end>-->
<!--          <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--        </template>-->
<!--      </Toolbar>-->
<!--    </div>-->
<!--  </div>-->



<!--  <div class="grid">-->
<!--      <div class="col-12">-->
<!--          <div class="card">-->
<!--              <Carousel :value="vocabularies" :numVisible="1" :numScroll="1" :responsiveOptions="carouselResponsiveOptions">-->
<!--                  <template #item="slotProps">-->
<!--                      <div class="border-1 surface-border border-round m-1 p-1">-->
<!--                          <div class="mb-3">-->
<!--                              <div class="relative mx-auto">-->
<!--                                  <img :src="'/images/vocabulary/' + slotProps.data.image" :alt="slotProps.data.name" class="w-full border-round" />-->
<!--                                  <Tag :value="slotProps.data.inventoryStatus" :severity="getSeverity(slotProps.data.inventoryStatus)" class="absolute" style="left: 5px; top: 5px" />-->
<!--                              </div>-->
<!--                          </div>-->
<!--                          <div class="flex align-items-center justify-content-center mb-3 font-bold">-->
<!--                            <h3><span class="first">{{ slotProps.data.name }} &nbsp;</span></h3>-->
<!--                            <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--                          </div>-->
<!--                          <div class="flex align-items-center justify-content-center mb-3 font-bold">-->
<!--                            <h3><span>{{ slotProps.data.chinese }}</span></h3>-->
<!--                          </div>-->
<!--                          <div class="flex align-items-center justify-content-center mb-3 font-bold">-->
<!--                            <h4 v-html="slotProps.data.sentence"></h4> &nbsp;&nbsp;-->
<!--                            <Button icon="pi pi-play" severity="info" rounded outlined class="mb-3 mr-3" />-->
<!--                          </div>-->
<!--                      </div>-->
<!--                  </template>-->
<!--              </Carousel>-->
<!--          </div>-->
<!--      </div>-->
<!--  </div>-->



<!--        <div class="col-12">-->
<!--            <div class="card">-->
<!--                <h5>Galleria</h5>-->
<!--                <Galleria :value="images" :responsiveOptions="galleriaResponsiveOptions" :numVisible="7"-->
<!--                    :circular="true" containerStyle="max-width: 800px; margin: auto">-->
<!--                    <template #item="slotProps">-->
<!--                        <img :src="slotProps.item.itemImageSrc" :alt="slotProps.item.alt"-->
<!--                            style="width: 100%; display: block" />-->
<!--                    </template>-->
<!--                    <template #thumbnail="slotProps">-->
<!--                        <img :src="slotProps.item.thumbnailImageSrc" :alt="slotProps.item.alt"-->
<!--                            style="width: 100%; display: block;" />-->
<!--                    </template>-->
<!--                </Galleria>-->
<!--            </div>-->
<!--        </div>-->
</template>

<style>
.first {
  color: #3B82F6;
  font-weight: bolder;
}
</style>