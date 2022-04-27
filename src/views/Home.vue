
<template>
  <div id="data-list-thumb-view" class="data-list-container">
    <vs-table pagination :max-items="itemsPerPage" search :data="listdata">
      <!-- ACTION - DROPDOWN -->
      <div slot="header" class="flex flex-wrap-reverse items-center flex-grow justify-between">
        <div class="vx-row">
          <div class="vx-col w-full">
            <v-select v-model="selected" :options="categories" :dir="$vs.rtl ? 'rtl' : 'ltr'" /><br>

          </div>
        </div>
      </div>
      <!-- ITEMS PER PAGE -->
      <template slot-scope="{data}">

        <div id="demo-basic-card">
          <div class="vx-row">
            <div class="vx-col w-full sm:w-1/2 lg:w-1/3 mb-base" :key="indextr" v-for="(d, indextr) in data">
              <!-- <div :key="index" v-for="(cate,index) in d.categories">
                 </div> -->

              <vx-card>
                <div v-if="selected===d.categories[0] || selected===d.categories[1]|| selected===d.categories[2] || selected==='all' ">
                  <!-- Narrower side column -->

                  <div class="flex mb-4">
                    <div class="w-1/4 bg-grid-color h-12">
                      <img :src="d.profile_image_url" style="width:50px; height:50px; object-fit:cover; border-radius:10px;">

                    </div>

                    <div class="w-3/4 bg-grid-color-secondary h-12" style="font-size:20px; font-weight:bold">{{d.name}}</div>
                  </div>

                  <!-- Wide center column -->

                  <div class="flex " style="padding-left:70px;">

                    <div class="w-2/2 bg-grid-color h-12" :key="index" v-for="(open,index) in d.operation_time[0].time_open">{{open}}</div>

                    <span class="w-2/2 bg-grid-color h-12">:AM</span>

                    <span class="w-2/2 bg-grid-color h-12">-</span>

                    <div class="flex ">
                      <div class="w-2/2 bg-grid-color h-12" :key="index" v-for="(close,index) in d.operation_time[0].time_close">{{close}}</div>
                      <span class="w-2/2 bg-grid-color h-12;" style="padding-right:60px;">:PM</span>

                    </div>

                    <div class="w-2/2 bg-grid-color h-12" style="padding-top:5px; padding-right:7px;">
                      <hr style="height:10px;border-width:0;border-radius: 30px;background-color: #134bba; width: 10px;">
                    </div>
                    <div class="w-2/2 bg-grid-color h-12">{{d.rating}}</div>

                  </div>

                  <br>
                  <div class="px-2">
                    <div class="flex -mx-2">
                      <div class="w-1/3 " v-for="img in d.images" :key="img">
                        <img :src=" img" style="width:100%; height:100px;  object-fit:cover;">
                      </div>

                    </div>
                  </div>
                </div>
              </vx-card>

            </div>
          </div>
        </div>

      </template>
    </vs-table>
  </div>
</template>

<script>
import vSelect from "vue-select";
import listdata from "../data/data.json";
export default {
  components: {
    vSelect,
  },
  data() {
    return {
      listdata,
      selected: [],
      itemsPerPage: 9,
      isMounted: false,
      categories: ["restaurant", "cafe", "bakery", "all"],
      selected: "all",
    };
  },
};
</script>

<style lang="scss">
#data-list-thumb-view {
  .vs-con-table {
    .product-name {
      max-width: 23rem;
    }

    .vs-table--header {
      display: flex;
      flex-wrap: wrap-reverse;
      margin-left: 1.5rem;
      margin-right: 1.5rem;
      > span {
        display: flex;
        flex-grow: 1;
      }

      .vs-table--search {
        padding-top: 0;

        .vs-table--search-input {
          padding: 0.9rem 2.5rem;
          font-size: 1rem;

          & + i {
            left: 1rem;
          }

          &:focus + i {
            left: 1rem;
          }
        }
      }
    }

    .vs-table {
      border-collapse: separate;
      border-spacing: 0 1.3rem;
      padding: 0 1rem;

      tr {
        box-shadow: 0 4px 20px 0 rgba(0, 0, 0, 0.05);

        td {
          padding: 10px;
          &:first-child {
            border-top-left-radius: 0.5rem;
            border-bottom-left-radius: 0.5rem;
          }
          &:last-child {
            border-top-right-radius: 0.5rem;
            border-bottom-right-radius: 0.5rem;
          }
          &.img-container {
            // width: 1rem;
            // background: #fff;

            span {
              display: flex;
              justify-content: flex-start;
            }

            .product-img {
              height: 110px;
            }
          }
        }
        td.td-check {
          padding: 20px !important;
        }
      }
    }

    .vs-table--thead {
      th {
        padding-top: 0;
        padding-bottom: 0;

        .vs-table-text {
          text-transform: uppercase;
          font-weight: 600;
        }
      }
      th.td-check {
        padding: 0 15px !important;
      }
      tr {
        background: none;
        box-shadow: none;
      }
    }

    .vs-table--pagination {
      justify-content: center;
    }
  }
}
</style>
