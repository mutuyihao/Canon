<template>
  <div class ="deleteBtnMain flex-row">
    <svg
      t="1648044329292"
      class="icon"
      viewBox="0 0 1024 1024"
      version="1.1"
      xmlns="http://www.w3.org/2000/svg"
      p-id="1113"
      :width="width"
      :height="height"
      @mouseenter="light()"
      @mouseleave="gray()"
    >
      <path
        d="M854.528 227.392l-167.04 0C684.48 136.704 610.176 64 518.72 64c-91.52 0-165.824 72.704-168.768 163.392l-180.48 0c-24.768 0-44.8 20.032-44.8 44.8L124.672 291.2c0 24.704 20.032 44.8 44.8 44.8l14.528 0 0 459.776c0 90.688 61.44 164.224 137.152 164.224l386.24 0c75.648 0 137.088-73.536 137.088-164.224L844.48 336l10.048 0c24.768 0 44.8-20.032 44.8-44.8L899.328 272.192C899.328 247.488 879.232 227.392 854.528 227.392zM518.72 169.216c33.28 0 60.608 25.6 63.488 58.176L455.232 227.392C458.048 194.816 485.376 169.216 518.72 169.216zM737.024 338.88l0 462.144c0 26.88-20.032 48.768-44.8 48.768L336.256 849.792c-24.768 0-44.736-21.888-44.736-48.768L291.52 338.88c0-0.96 0.064-1.92 0.128-2.88l445.248 0C736.896 336.96 737.024 337.92 737.024 338.88z"
        p-id="5141"
        :fill="btnColor"
      ></path>
      <path
        d="M381.056 731.072c19.776 0 35.84-16 35.84-35.776L416.896 490.432c0-19.84-16.064-35.84-35.84-35.84-19.84 0-35.904 16-35.904 35.84l0 204.864C345.216 715.072 361.28 731.072 381.056 731.072z"
        p-id="5142"
        :fill="btnColor"
      ></path>
      <path
        d="M511.104 731.072c19.776 0 35.776-16 35.776-35.776L546.88 490.432c0-19.84-16-35.84-35.776-35.84-19.84 0-35.904 16-35.904 35.84l0 204.864C475.264 715.072 491.328 731.072 511.104 731.072z"
        p-id="5143"
        :fill="btnColor"
      ></path>
      <path
        d="M647.616 731.072c19.84 0 35.84-16 35.84-35.776L683.456 490.432c0-19.84-16-35.84-35.84-35.84s-35.776 16-35.776 35.84l0 204.864C611.904 715.072 627.84 731.072 647.616 731.072z"
        p-id="5144"
        :fill="btnColor"
      ></path>
    </svg>
    <span @mouseenter="light()"
      @mouseleave="gray()" class="deleteBtnText"><slot ></slot></span>
    
  </div>
</template>

<script>
export default {
  name: "deleteBtn",
  components: {},
  props: {
    color: "",
    width: "",
    height: "",
    lightColor: "",
    deepColor: "",
  },
  data() {
    return {
      btnColor: "#9b9b9b",
      song: this.$store.state.songConfig,
      clickSong: {},
      lightC: "",
      deepC: "",
      type: "",
    };
  },
  watch: {
  },
  computed: {},
  methods: {
    light() {
      this.btnColor = this.lightC;
    },
    gray() {
      this.btnColor = this.deepC;
    },
    init() {
      this.type = this.typeBtn;
      this.btnColor = this.color;
      this.lightC = this.lightColor;
      this.deepC = this.deepColor;
    },
  },
  created() {
    this.init();
  },
  mounted() {
  },
};
</script>
<style scoped>

.deleteBtnMain{
  align-items:center;
}
.deleteBtnText:hover{
  text-decoration:underline;
}

</style>