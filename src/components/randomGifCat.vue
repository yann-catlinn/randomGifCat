<template>
<div id="app">
    <div class="container-fluid">
        <div class="row lightblue pt-5 pb-2 text-center">
            <div class="col-sm-6 col-md-6 col-lg-6 mx-auto">
                <h1>Random Gif Cat</h1>
            </div>
        </div>
        <div class="row rose pt-2 pb-2">
            <div class="col-sm-6 col-md-6 col-lg-6 mx-auto">
                <form class="d-inline-flex flex-column">
                <div class="form-group d-inline-flex">
                    <label for="exampleFormControlInput1">Título:</label>
                    <input type="text" class="form-control ml-2" id="exampleFormControlInput1" placeholder="Escribe un título" v-model="title" ref="title">
                </div>
                <div class="form-group d-inline-flex">
                    <label for="inputState">Filtro:</label>
                    <select class="form-control ml-2" id="inputState" @change="changeFilter($event)">
                    <option v-for="opt in filters" :key="opt" :value="opt" v-text="opt"></option>
                    </select>
                </div>
                <div class="form-group d-inline-flex">
                    <label for="inputState">Color:</label>
                    <select class="form-control ml-2" id="inputState" @change="changeColor($event)">
                     <option v-for="color in colors" :key="color.color" :value="color.value" v-text="color.color"></option>
                    </select>
                    <span :style="style" id="circle"></span>
                </div>
                <div class="form-group d-inline-flex">
                    <label for="exampleFormControlInput1">Tamaño:</label>
                    <input type="text" class="form-control ml-2" id="exampleFormControlInput1" placeholder="Ingresa el tamaño de texto" v-model="size" ref="size">
                </div>
                
                </form>
            </div>
        </div>
        <div class="row lightblue pt-2 pb-5 d-flex flex-column">
            <div class="col-sm-6 col-md-6 col-lg-6 mx-auto d-flex flex-column justify-content-center">
            <button @click="getRandomCat" type="button" class="btn btn-light mx-auto">Obtener mi gatito</button>
            <img class="my-3" :src="url">
            </div>
        </div>
    </div>
    
  
</div>
  
</template>

<script>
  export default {
      name: 'randomGifCat',
      //props: {},
    data: function() {
      return {
          title:"",
            size:"",
             myFilter:{
                filter: "",
            },
            filters:[
            "blur",
            "mono",
            "sepia",
            "negative",
            "paint",
            ],
            selected:"",
            url:"",
            colors:[
                {color:"rojo", value:"red"},
                {color:"azul", value:"blue"},
                {color:"verde", value:"green"},
                {color:"blanco", value:"white" },
                {color:"amarillo",value:"yellow"},
            ],
            style:{
                background:""
            } 
      }
    },
    // computed: {},
    methods: {
            changeColor(e){
            this.style.background=e.target.value            
        },
            changeFilter(e){
            var response= e.target.value
            if(response==="blur"){
            this.selected="blur"
            
            console.log(this.selected)
            }else if(response==="mono"){
                this.selected="mono"
                console.log(this.selected)
                
            }else if(response==="negative"){
                this.selected="negative"
                console.log(this.selected)
              
            }else if(response==="paint"){
                this.selected="paint"
                console.log(this.selected)
               
            }else if(response==="sepia"){
                this.selected="sepia"
                console.log(this.selected)

            }
                return 
                selected,url
            },
            getRandomCat(){
                if (this.size>1000 || this.size<1 || isNaN(this.size)){
                    alert("Ingrese un número entre 1 y 1000")
                    this.$refs.size.value=""
                    this.$refs.size.focus()
                }else if(this.title===""){
                        alert("Ingrese un título")
                        this.$refs.title.focus()
                }
                else
                this.url=`https://cataas.com/cat/gif/says/${this.title}?filter=${this.selected}&color=${this.style.background}&size=${this.size}&type=or`
            }
    },
    //components: {},
  }
</script>

<style scoped>
    body{
        background-color: lightblue !important;
        }
    
  #app {
  /*  font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    background: lightblue;
    */
    color: #2d2d2d;
  }
  .lightblue{
      background-color: lightblue;

  }
  .rose{
      background-color: lightcoral;
  }
    #circle{
        width:40px;
        height: 40px;
        display:inline-block;
        border-radius:50%;
        margin-left: 20px;
    }
    button{
        width: fit-content;
    }
    select{
        width: max-content;
    }
</style>