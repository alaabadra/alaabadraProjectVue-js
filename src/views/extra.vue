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
        <button
          class="btn col-sm-2 ml-auto btn-outline-primary mt-5"
          @click="addNew()"
          style="max-height: 3rem !important"
        >
          add new
        </button>
        <div class="col-sm-9 mr-auto row mt-3 customRow2">
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
            @drop="getFile(e)"
            @dragover="allowDrop(event)"
          >
            <span class="w-100 badge badge-pill bg-light"
              >Drop Your File Here</span
            >
            <i class="fas fa-file fa-6x" style="color: grey"></i>
          </button>
          <input type="file" hidden ref="fileUpload" accept=".pdf,.doc,.docx" />
          <div class="col-sm-9 ml-auto row customRow"></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { VueEditor } from "vue2-editor";
export default {
  components: {
    VueEditor
  },
  data() {
    return {
      content: null,
      chunck: null,
      items: [],
      option1: null,
      option2: null,
      file: null,
      x: null
    };
  },
  methods: {
    onChange() {
      this.filelist = [...this.$refs.file.files];
    },
    remove(i) {
      this.filelist.splice(i, 1);
    },

    getFile(e) {
      this.$refs.fileUpload.files[0] = e.dataTransfer.files;
    },
    allowDrop(event) {
      event.preventDefault();
    },
    addToArray() {
      if (this.x != null) {
        this.items.push(this.x.value);
      }
    },
    openFile() {
      let fileUpload = this.$refs.fileUpload;
      fileUpload.click();
      fileUpload.addEventListener("change", e => {
        this.file = e.target.files[0];
        const reader = new FileReader();
        if (this.$refs.fileName) {
          this.$refs.fileName.innerHTML = this.file.name;
        }
        reader.addEventListener("load", () => {
          //    = e.target.result;
        });
        reader.readAsDataURL(this.file);
      });
    },
    addNew() {
      let row = document.querySelector(".customRow2"),
        child1 = document.createElement("div"),
        child = ` 
          <div class="input-group col-sm-3 mx-auto p-0 rounded-lg">
           <div class="input-group-prepend">
             <button class="btn btn-outline-primary" type="button""
              id="button-addon1"><i class="fas fa-plus-circle fa-lg"></i></button>
             </div>
          <input type="text"  list="i1"
           class="form-control chunck" 
           placeholder="" 
           aria-label="Example text with button addon"
            aria-describedby="button-addon1"
            id="chunk"
            ref="choose">
          </div>
          <datalist id="i1">
            
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
          </datalist>`;
      child1.setAttribute("class", "col-sm-12 mx-auto row mt-2");
      child1.innerHTML = child;
      row.appendChild(child1);
      setTimeout(() => {
        let btn = document.getElementById("button-addon1"),
          i1 = document.getElementById("i1"),
          opt = document.createElement("option");
        this.x = document.getElementById("chunk");
        btn.addEventListener("click", () => {
          this.addToArray();
        });
        this.items.forEach(item => {
          opt.setAttribute("value", item);
          i1.appendChild(opt);
        });
      }, 500);
    }
  },
  watch: {
    option1(val) {
      if (val == "Excutive Summary") {
        this.option2 = "All Members";
      } else if (val == "Power Point Presentation") {
        this.option2 = "NDA Only";
      } else {
        this.option2 = "Investors";
      }
    },
    file(val) {
      console.log(val.name);
      let row = document.querySelector(".customRow"),
        el = document.createElement("div");
      el.setAttribute("class", "col-sm-12 mx-auto row");
      row.appendChild(el);
      el.innerHTML = `<select
              name=""
              id=""
              class="col-sm-3 mx-auto form-control"
              v-model="option1"
            >
              <option value="Excutive Summary">Excutive Summary</option>
              <option value="Power Point Presentation"
                >Power Point Presentation</option
              >
              <option value="PPM & Sub Docs">PPM & Sub Docs</option>
            </select>
            <select
              name=""
              id=""
              class="col-sm-3 mx-auto form-control"
              v-model="option2"
            >
              <option value="All Members">All Members</option>
              <option value="NDA Only">NDA Only</option>
              <option value="Investors">Investors</option>
            </select>
            <div
              class="col-sm-4 rounded-pill form-control mx-auto bg-light cust"
              ref="fileName"
              style="font-size: .8rem"
            >${val.name}</div>`;
      setTimeout(() => {
        let cust = document.querySelector(".cust");
        cust.addEventListener("click", () => {
          this.openFile();
        });
      }, 350);
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
