<template>
  <div >
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
            @click="playMusic()"
          >
            <path
              d="M512 62.389956c-248.312412 0-449.610044 201.297632-449.610044 449.610044s201.297632 449.610044 449.610044 449.610044 449.610044-201.297632 449.610044-449.610044S760.312412 62.389956 512 62.389956zM786.507004 786.507004c-35.672454 35.672454-77.196173 63.672158-123.416867 83.222423-47.821145 20.22667-98.655927 30.482245-151.09116 30.482245-52.435233 0-103.270015-10.255575-151.09116-30.482245-46.220694-19.549242-87.744413-47.549969-123.416867-83.222423-35.672454-35.672454-63.672158-77.196173-83.222423-123.416867-20.22667-47.821145-30.482245-98.655927-30.482245-151.090137 0-52.435233 10.255575-103.270015 30.482245-151.09116 19.549242-46.220694 47.549969-87.744413 83.222423-123.416867 35.672454-35.672454 77.196173-63.672158 123.416867-83.222423 47.821145-20.22667 98.654904-30.482245 151.09116-30.482245 52.435233 0 103.268992 10.255575 151.09116 30.482245 46.220694 19.549242 87.744413 47.549969 123.416867 83.222423 35.672454 35.672454 63.672158 77.196173 83.222423 123.416867 20.22667 47.821145 30.482245 98.655927 30.482245 151.09116 0 52.435233-10.255575 103.268992-30.482245 151.090137C850.179163 709.310831 822.179458 750.83455 786.507004 786.507004z"
              p-id="1114"
              :fill="btnColor"
            ></path>
            <path
              d="M727.558427 506.975567l-334.355067-252.891707c-3.868097-2.232854-8.702196 0.558725-8.702196 5.024433l0 505.782392c0 4.465708 4.834098 7.257288 8.702196 5.024433l334.355067-252.890684C731.426525 514.791579 731.426525 509.208421 727.558427 506.975567z"
              p-id="1115"
              :fill="btnColor"
            ></path>
          </svg>
  </div>
</template>

<script>
export default {
  name:'playBtn',
  components: {},
  props: {
    color:"",
    width:"",
    height:"",
    lightColor:"",
    deepColor:"",
    songConfig:{},
    typeBtn:{
      type:String,
      default:"song"
    }
  },
  data() {
    return {
      btnColor:"#b3b3b3",
      song:this.$store.state.songConfig,
      clickSong:{},
      lightC:"",
      deepC:"",
      type:""

    };
  },
  watch: {
    "$store.state.songConfig"(newVal){
      if(this.type=="song"){
      this.song = newVal
      }
    },
    songConfig(){
      if(this.type=="song"){
      this.clickSong = this.songConfig
      }
    },
    "$store.state.currentTime"(){
      if(this.type=="song"){
        if(this.song.id == this.clickSong.id){
          this.btnColor="#cc1111"
          this.lightC="#cc1111"
          this.deepC="#cc1111"
        }else{
          this.btnColor=this.color
          this.lightC=this.lightColor
          this.deepC=this.deepColor
        }
    }
    }
  },
  computed: {},
  methods: {
     light() {
      this.btnColor = this.lightC;
    },
    gray() {
      this.btnColor = this.deepC;
    },
    init(){
      this.type=this.typeBtn
      this.btnColor=this.color
      if(this.type=="song"){
        this.clickSong = this.songConfig
        }
      this.lightC=this.lightColor
      this.deepC = this.deepColor
    },
    defineColor(){
      if(this.type=="song"){
        if(this.song.id == this.clickSong.id){
        this.btnColor="#cc1111"
        this.lightC="#cc1111"
        this.deepC="#cc1111"
      }
    } 
    },
    playMusic(){
      this.$store.dispatch("updateMusic",this.clickSong)
      this.btnColor="#cc1111"
    },
  },
  created() {
    this.init()
  },
  mounted() {
    this.defineColor()
  }
};
</script>
<style scoped>
svg{
  cursor:pointer;
}
</style>