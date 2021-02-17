<template>
  <div>
    <div class="container-fluid p-5">
      <div class="row">
        <label for="" class="col-sm-7 mr-auto text-left mt-1 hw">
          Company Information
        </label>
        <div class="col-sm-11 mr-auto row mt-3">
          <input
            type="text"
            class="col-sm-3 mx-auto form-control rounded-lg"
            placeholder="Company Name"
          />
          <input
            type="text"
            class="col-sm-3 mx-auto form-control rounded-lg"
            placeholder="Company Website"
          />
          <input
            type="text"
            class="col-sm-3 mx-auto form-control rounded-lg"
            placeholder="Company HQ County"
          />
        </div>
        <label for="" class="col-sm-4 mr-auto text-left mt-4 hw">
          Raise Information
        </label>
        <label class="col-sm-8 ml-auto text-left mt-5 p-0">
          Will show progress against these numbers
        </label>
        <div class="col-sm-10 mr-auto row ">
          <div class="col-sm-4 mr-auto row">
            <input
              type="text"
              class="col-sm-5 mx-auto form-control rounded-lg"
              placeholder="Company Website"
            />
            <input
              type="text"
              class="col-sm-5 mx-auto form-control rounded-lg"
              placeholder="Company Website"
            />
          </div>
          <!--/////-->
          <div class="col-sm-8 ml-auto row">
            <input
              type="text"
              class="col-sm-3 mx-auto form-control rounded-lg"
              placeholder="Company Website"
            />
            <input
              type="text"
              class="col-sm-3 mx-auto form-control rounded-lg"
              placeholder="Company Website"
            />
            <input
              type="text"
              class="col-sm-3 mx-auto form-control rounded-lg"
              placeholder="Company Website"
            />
          </div>
        </div>
        <!--/////-->
        <label class="col-sm-8 mr-auto text-left mt-3 hw">
          Oportunity Information
        </label>
        <div class="col-sm-7 mr-auto row mt-2">
          <input
            type="text"
            class="col-sm-7 mr-auto form-control rounded-lg"
            placeholder="Company Website"
          />
          <input
            type="text"
            class="col-sm-4 ml-auto form-control rounded-lg"
            placeholder="Company Website"
          />
        </div>
        <vue-editor
          id="editor1"
          v-model="content"
          class="col-sm-9 mr-auto mt-3 p-0 mb-5"
        ></vue-editor>
        <!--/////-->
        <label class="col-sm-8 mr-auto text-left mt-5 hw">
          Oportunity Information
        </label>
        <div class="col-sm-9 mr-auto row mt-3">
          <b-input-group class="col-sm-3 mx-auto p-0 rounded-lg">
            <b-form-input v-model="chunck" list="i1"></b-form-input>
            <template #append>
              <b-input-group-text
                ><strong
                  class="text-primary btn btn-sm p-0"
                  @click="addToArray()"
                >
                  <i class="fas fa-plus-circle fa-lg"></i> </strong
              ></b-input-group-text>
            </template>
          </b-input-group>

          <datalist id="i1">
            <option
              v-for="(item, index) in items"
              :key="index"
              :value="item"
            ></option>
          </datalist>
          <!-- //// -->
          <input list="i2" class="col-sm-3 mx-auto form-control rounded-lg" />

          <datalist id="i2"> </datalist>
          <!-- //// -->
          <input list="i3" class="col-sm-3 mx-auto form-control rounded-lg" />

          <datalist id="i3">
            <option value="All Members"></option>
            <option value="NDA only"></option>
            <option value="Investors"></option>
          </datalist>
          <!-- //// -->
        </div>
        <!--/////-->
        <label class="col-sm-8 mr-auto text-left mt-5 hw">
          Oportunity Resources
        </label>
        <div class="col-sm-12 mr-auto row">
          <button
            class="btn col-sm-3 mr-auto"
            style="height: 200px !important; border: 1px dotted blue"
            @click="openFile()"
          >
            <span class="w-100 badge badge-pill bg-light"
              >Drop Your File Here</span
            >
            <i class="fas fa-file fa-6x" style="color: grey"></i>
          </button>
          <input type="file" hidden ref="fileUpload" accept=".pdf" />
          <div class="col-sm-9 ml-auto row">
            <select name="" id="" class="col-sm-3 mx-auto form-control" v-model="option1">
              <option value="Excutive Summary">Excutive Summary</option>
              <option value="Power Point Presentation"
                >Power Point Presentation</option
              >
              <option value="PPM & Sub Docs">PPM & Sub Docs</option>
            </select>
            <select name="" id="" class="col-sm-3 mx-auto form-control"  v-model="option2">
              <option value="All Members">All Members</option>
              <option value="NDA Only"
                >NDA Only</option
              >
              <option value="Investors">Investors</option>
            </select>
            <div
              class="col-sm-4 rounded-pill form-control mx-auto bg-light"
              ref="fileName"
              style="font-size: .8rem"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { VueEditor } from "vue2-editor";
export default {
  components: {
    VueEditor,
  },
  data() {
    return {
      content: null,
      chunck: null,
      items: [],
      option1: null,
      option2: null
    };
  },
  methods: {
    addToArray() {
      this.items.push(this.chunck);
    },
    openFile() {
      let fileUpload = this.$refs.fileUpload;
      fileUpload.click();
      fileUpload.addEventListener("change", (e) => {
        const file = e.target.files[0];
        const reader = new FileReader();
        this.$refs.fileName.innerHTML = file.name;
        reader.addEventListener("load", () => {
        //    = e.target.result;
        });
        reader.readAsDataURL(file);
      });
    },
  },
  watch:{
      option1(val){
          if(val== "Excutive Summary"){
              this.option2 = "All Members"
          }else if(val== "Power Point Presentation"){
              this.option2 = "NDA Only"
          }else{
               this.option2 = "Investors"
          }
      }
  }
};
</script>
<style scoped>
.hw {
  font-size: 1.5rem;
  font-weight: 700;
}
.ql-container {
  height: 50px !important;
  max-height: 50px !important;
}
.ql-editor {
  min-height: 100px !important;
  height: 100px !important;
}
</style>
