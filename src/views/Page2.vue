<template>
  <div id="data-list-thumb-view" class="data-list-container">
    <vs-table pagination :max-items="itemsPerPage" search :data="listdata" v-model="currentx">
      <div slot="header" class="flex flex-wrap-reverse items-center flex-grow justify-between">
        <div class="vx-row">
          <div class="vx-col w-full">
            <vs-button style="margin-bottom:6px;" @click="currentx--">back</vs-button>
            <!-- <vs-pagination :total="5" v-model="currentx"></vs-pagination> -->
          </div>
        </div>
      </div>
      <template slot-scope="{data}">
        <vs-row vs-w="12" :key="indextr" v-for="(d, indextr) in data">
          <vx-card style="background-color:#C4D3E9; ">

            <vs-col vs-type="flex" vs-align="center" vs-w="6">
              <vx-card>
                <div slot="no-body" style="border-radius:10px;">
                  <img :src="d.profile_image_url" style="width:100%; height:30rem; object-fit:cover; border-radius:5px; ">
                </div>
                <h5 class="mb-2"></h5>
                <p class="text-grey"></p>
                <p class="text-grey"></p>
                <div class="flex justify-between flex-wrap">
                  <vs-button class="mt-4 mr-2 shadow-lg" type="gradient" color="#7367F0" gradient-color-secondary="#CE9FFC">Download</vs-button>
                  <vs-button class="mt-4" type="border" color="#b9b9b9">View All</vs-button>

                </div>
                <div class="flex ">
                  <vs-button class="mt-4 mr-2 shadow-lg" type="gradient" color="#7367F0" gradient-color-secondary="#CE9FFC">Download</vs-button>
                  <vs-button class="mt-4" type="border" color="#b9b9b9">View All</vs-button>

                </div>
                <div class="flex ">
                  <vs-button class="mt-4 mr-2 shadow-lg" type="gradient" color="#7367F0" gradient-color-secondary="#CE9FFC">Download</vs-button>
                  <vs-button class="mt-4" type="border" color="#b9b9b9">View All</vs-button>

                </div>
              </vx-card>

            </vs-col>

            <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="6" style="padding-left:30px;">
              <vx-card style="margin-bottom:50px;">
                <div v-for="img in d.images" :key="img">
                  <img :src=" img" style="width:100%; height:250px;  object-fit:cover;">
                </div>

              </vx-card>
            </vs-col>
          </vx-card>
        </vs-row>

      </template>
    </vs-table>
  </div>
</template>

<script>
import listdata from "../data/data.json";
import VxCard from "../components/vx-card/VxCard.vue";
export default {
  components: { VxCard },
  data() {
    return {
      listdata,
      selected: [],
      itemsPerPage: 1,
      currentx: 5,
    };
  },
};
</script>

<style>
</style>