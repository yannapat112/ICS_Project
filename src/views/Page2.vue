<template>
  <div id="data-list-thumb-view" class="data-list-container">
    <vs-table pagination :max-items="itemsPerPage" search :data="listdata" v-model="currentx">
      <div slot="header" class="flex flex-wrap-reverse items-center flex-grow justify-between">
        <div class="vx-row">
          <div class="vx-col w-full">
          
            <!-- <vs-button style="margin-bottom:6px;" @click="currentx--">back</vs-button> -->
            <!-- <vs-pagination :total="5" v-model="currentx"></vs-pagination> -->
          </div>
        </div>
      </div>
      <template slot-scope="{data}">
        <vs-row vs-w="12" :key="indextr" v-for="(d, indextr) in data">
          <vx-card style="background-color:#C4D3E9;  ">

            <vs-col vs-type="flex" vs-align="center" vs-w="6">
              <vx-card style="padding-bottom:5%">
                <div slot="no-body" style="border-radius:10px;">
                  <img :src="d.profile_image_url" style="width:100%; height:30rem; object-fit:cover; border-radius:5px; ">
                </div>
                <div class="flex flex-wrap">
                  <div style="padding-right:65%; font-weight:bold; font-size:120%;">{{d.name}}</div>
                  <div class="w-2/2 bg-grid-color h-12" style="padding-top:5px; padding-right:7px;">
                    <hr style="height:10px;border-width:0;border-radius: 30px;background-color: #134bba; width: 10px;">
                  </div>
                  <div class="w-2/2 bg-grid-color h-12">{{d.rating}}</div>

                </div>
                <div class="flex flex-wrap">
                  <div style="padding-right:10%; font-weight:bold;">ADRESS:</div>
                  <div class="w-1/2 bg-grid-color ">
                    {{d.address}}

                  </div>

                </div>

                <div class="flex flex-wrap" style="padding-right:10%; font-weight:bold;">Opening Hour:</div>
                <vs-row :key="index" v-for="(time,index) in d.operation_time">
                  <vs-col vs-type="flex" vs-justify="center" vs-align="center">
                  <div  >{{time.day}}</div>
                   <div style="padding-left:10%;"> {{time.time_open}}:AM</div>
                       <div style="padding-left:2%;"> -</div>
                   <div style="padding-left:2%;"> {{time.time_close}}:PM</div>
                  </vs-col>
                </vs-row>

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