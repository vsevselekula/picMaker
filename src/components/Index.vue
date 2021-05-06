
<template>
<div class="mainContent" >
  <!-- <div class="picContainer" id="capture" >
    <div class="picMessage" contenteditable="true">
    Пиши тут что хочешь      
        <img class="fullPreview" :src="src"/>

    </div>  
  </div> -->
  <div class="picWrapper" id="capture" >
<div class="preview"
       :style="{ 'background-image': 'url(' + src + ')' }" >
  </div>
  <div class="picText" contenteditable="true" >
       пиши тут че каво
  </div>
  </div>
     
  <div class="thumbnailsContainer">
<div class="thumbnails">
<img src="../assets/images/1.png" class="thumb" @click="copySrc"/>
    <img src="../assets/images/2.png" class="thumb" @click="copySrc"/>
<img src="../assets/images/3.png" class="thumb" @click="copySrc"/>
    <img src="../assets/images/1.png" class="thumb" @click="copySrc"/>
    <img src="../assets/images/2.png" class="thumb" @click="copySrc"/>
<img src="../assets/images/3.png" class="thumb" @click="copySrc"/>
<img src="../assets/images/1.png" class="thumb" @click="copySrc"/>
    <img src="../assets/images/2.png" class="thumb" @click="copySrc"/>
<img src="../assets/images/3.png" class="thumb" @click="copySrc"/>
  </div>
  </div>
  
  <div class="controls">
    <button v-on:click="renderPic" class="trigger">Скачать картинку
    
    </button>
  </div>
  </div>
</template>

<script>
import html2canvas from 'html2canvas'

export default {
  data: function() {
    return {
        src: "'../assets/images/3.png'",
    }
  },
  methods: {
    copySrc: function(img){
            this.src = img.srcElement.src;
        },
  renderPic: function () {
     html2canvas(document.querySelector("#capture"), {scale: 2}).then(i => {
    saveAs(i.toDataURL(), 'вакансия.png');
    })
    function saveAs(uri, filename) {

    var link = document.createElement('a');

    if (typeof link.download === 'string') {

        link.href = uri;
        link.download = filename;

        //Firefox requires the link to be in the body
        document.body.appendChild(link);

        //simulate click
        link.click();

        //remove the link when done
        document.body.removeChild(link);

    } else {

        window.open(uri);

    }
}
  }
  }
}
</script>

<style>
.mainContent {
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: center;
    flex-direction: column;
        align-items: center;

}
.picContainer{
        width: 500px;
    height: 500px;
    position: relative;
    background-color: #EAE5DB;
}
.controls{
  margin-top: 15px
}
.trigger{
     background: #00AAFF;
    border-radius: 50px;
    font-size: 15px;
    border: none;
    padding: 15px 20px;
    font-family: 'Lato';
    color: white;
}
.picMessage{
    word-break: break-word;
    width: 100%;
    white-space: normal;
    text-align: center;
    font-size: 42px;
    font-family: Lato;
    font-weight: bold;
}
.thumbnailsContainer {
overflow-x: scroll;
    overflow-y: hidden;
    height: auto;
    width: 500px;
}

.thumbnails {
    width: auto;
    white-space: nowrap;
    margin-top: 15px;
    padding-bottom: 10px;
}
.preview{
width: 500px;
height: 500px;
background-size:cover;
  text-align:center;
  display:table-cell;
  vertical-align:middle;
    font-size: 42px;
    font-family: Lato;
    font-weight: bold;
        background-color: #EAE5DB;

}
.thumb {
display: inline-block;
    background-color: #f77177;
    border: 1px solid white;
    width: 50px;
    height: 50px;
    margin-right: 7px;
    border-radius: 10px;
}
/* .thumb{
  width: 50px;
    height: 50px;
    background-color: burlywood;
    border-radius: 5px;

    /* margin-right: 10px; */
/* } */
/* .thumbnails{

    margin-top: 15px;
    display: flex;
    justify-content: flex-start;
    width: 500px; */
/* } */ 
.picWrapper{
  position: relative;
}
.picText{
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  width: 450px;
    font-size: 42px;
    font-family: Lato;
    font-weight: bold;
}
.fullPreview {
    width: 500px;
    height: 500px;
    position: absolute;
    top: 0px;
    left: 0px;
}
</style>
<style>
  @font-face {
    font-family: Lato;
    src: url('../assets/Lato-Regular.ttf');
    font-weight: normal;
  }
  @font-face {
    font-family: Lato;
    src: url('../assets/Lato-Bold.ttf');
    font-weight: Bold;
  }
  @font-face {
    font-family: Euclid;
    src: url('../assets/EuclidCircularB-Bold.otf');
    font-weight: bold;
  }
  @font-face {
    font-family: Euclid;
    src: url('../assets/EuclidCircularB-Regular.otf');
    font-weight: normal;
  }
</style>
