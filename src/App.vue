<template>
  <div id="app">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Asul& family=Kodchasan:wght@200&family=Great+Vibes&family=ABeeZee:ital@1&family=Baloo+Tammudu+2&family=Mulish:wght@300&family=Tenali+Ramakrishna&display=swap" rel="stylesheet" />
   <link  rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.14.0/css/all.css" />
   <link href="https://fonts.googleapis.com/css2? amily=Baloo+Thambi+2:wght@500&family=Montaga&family=Tajawal&display=swap" rel="stylesheet">
        
        <div class="header">
            <img class="header_icon" src="https://seeklogo.com/images/A/airbnb-logo-3023AC4CBA-seeklogo.com.png" />
           
     <div class="header_center">
        <div @click="showLocation=!showLocation"  class="header_center location">
                   <label style="display:block;font-family: 'ABeeZee', sans-serif;margin-top:-1.5rem;margin-left:1rem;">Location</label> <br>   
                   <input :class="active" v-model="search" @keyup.enter="addPlace"  type="text"  style="display:block; margin-top:2rem;margin-left:-4.1rem;" placeholder="Where are you going?">
         </div>
         
          <div v-if="showLocation" class="search_list">
             <div  style="margin-left:16rem;" class="close_btn">
              <button @click="showLocation=!showLocation" v-if="showLocation===true" class="close"> <i id="close" class="fas fa-times"></i>
                </button>   </div>
                   <div class="autocom_box">
                       <li  v-for="place in filteredPlaces" :key="place"><i class="fas fa-map-marker-alt place" style="color:gray;font-size:18px;margin-right:0.5rem;"></i> {{place.country}} , {{place.city}}</li>
                   </div>
           </div>
      
               <div @click="showGuest=!showGuest" class="header_center location">
                <label style="display:block;font-family: 'ABeeZee', sans-serif; margin-top:-1.5rem;margin-left:1rem;">Guests</label> <br>    
               <button class="add_guest" @click="showCart =!showCart"> <br> <button @click="showGuest=!showguest" v-if="showGuest===false" class="add_guest">Add guest</button> 
                <h6 class="guest" v-if="showGuest">guest {{totalAge}} </h6>   </button> 
               </div>
                  <i class="fas fa-search"  v-if ="showSearch===false" @click="showSearch =!showSearch" id="icon"></i>
                   <button @click="saveSession()" class="search" v-if="showSearch"> <img  style="width:30px;height:30px;margin:1rem;margin-left:-1rem;" :src="'http://gifimage.net/wp-content/uploads/2018/04/loading-gif-orange-8.gif'" alt=""> <span v-if="loading" style="padding:3px;"></span>Search</button>
          </div>

           
  <div  v-if="showCart" class="cart-dropdown">
      <div class="close_btn">
      <button @click="showCart=!showCart" v-if="showCart===true" class="close"> <i id="close" class="fas fa-times"></i>
      </button>
       </div>
       <div v-for="product in products" :key="product.id" class="items">
          <h6>{{ product.name }}</h6>
          <p> {{product.detail}} </p>
      <div class="guest_btn">
      <button @click="updateCart(product, 'subtract')" class="decrease">-</button>
      <h4 id="number" style="text-decoration:none;"> {{product.age}}</h4>
      <button  @click="updateCart(product, 'add')" class="increase">+</button>
      </div>
     
    </div>
    </div>
   
   
    
              
               <div class="header_right">
                 <p>Become a host</p>
                 <i class="fas fa-globe"></i>
                 <i class="fas fa-angle-down"></i>
                 <i class="fas fa-user-circle"></i>
              </div>
        </div>
       
    

 <div class="home">
    <Banner></Banner>
       <div class="home_section">
         <Card :details="details"/> 
         <Card :objects="objects" />
         <Card :images="images" />
       </div>
   </div>
   <Search />
    <Result image="https://tse4.mm.bing.net/th?id=OIP.Zi2CHgsrNrdltGCFWyjtcQHaEK&pid=Api&P=0&w=277&h=157"
                 location="Private room in center of London"
                 title="Stay at this spacious Edwardian House"
                 description="1 guest . 1 bedroom . 1 bed . 15 shared bthrooms . wifi . kitchen . Free parking . washing Machine"
                 star="4.73"
                 price="$30 / night"
                 total="$117 total" />

        <Result image="https://tse1.mm.bing.net/th?id=OIP.jXwnYZ1tWuYtUtNLTJiJVAHaEK&pid=Api&P=0&w=299&h=169"
                location="Treehouse in Bengaluru"
                 title="Tree House close to Bangalore"
                 description="1 guest . 1 bedroom . 1 bed . 15 shared bthrooms . wifi . kitchen . Free parking . washing Machine"
                 star="4.83"
                 price="$20 / night"
                 total="$98 total" />
                 
        <Result image="https://vishrantiresorts.com/en/wp-content/uploads/2019/11/Vishranti7.jpg"         location="Entire bungalow in Mukteshwar"
                 title="Luxury Himalayan Home 'Iris Cottage' "
                 description="1 guest . 1 bedroom . 1 bed . 15 shared bthrooms . wifi . kitchen . Free parking . washing Machine"
                 star="4.70"
                 price="$40 / night"
                 total="$130 total" />

     <Footer />

    
  </div>

</template>

<script>
import Card from './components/Card.vue'
import Banner from './components/Banner.vue'
import Footer from './components/Footer'
import Result from './components/Result'
import Search from './components/Search'

export default {
 components: {
    
    Footer,
    Banner,
    Card,
    Result,
    Search
  },
  data(){
     return{
          search:'',
          idForPlace:3,
          loading:false,
          places:[
{city:"Meipu",country:"China"},
{city:"Hanchang",country:"China"},
{city:"Qaffīn",country:"Palestinian Territory"},
{city:"Mikró Monastíri",country:"Greece"},
{city:"Steblevë","country":"Albania"},
{city:"Arai",country:"Japan"},
{city:"Antimácheia",country:"Greece"},
{city:"Bršadin",country:"Croatia"},
{city:"Ḩammām Damt",country:"Yemen"},
{city:"Kuandian",country:"China"},
{city:"Bichura",country:"Russia"},
{city:"Halinów",country:"Poland"},
{city:"Göteborg",country:"Sweden"},
{city:"Tomepampa",country:"Peru"},
{city:"Jetis",country:"Indonesia"},
{city:"Palaiópyrgos",country:"Greece"},
{city:"Opol",country:"Philippines"},
{city:"Mueang Nonthaburi",country:"Thailand"},
{city:"Kutno",country:"Poland"},
{city:"Gotputuk",country:"Indonesia"},

          ],
      
details:[
          {src:'https://img5.goodfon.com/wallpaper/nbig/f/f6/interer-pentkhaus-gostinaia-prostranstvo-luxury-penthouse-in.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.40'},
          {src:'https://i.pinimg.com/originals/94/db/d1/94dbd1cb0573dac7bcc1af0f51e2d1ac.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylish room in design district', star:'4.25'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21603/stockernumber2160300034/53564553-bedroom-interior-3d-illustration.jpg', title:'Entire house', spaciality:'Mordern House in a remote area', star:'4.96'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21702/stockernumber2170200063/70876514-interior-dining-area-3d-illustration.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.85'},
          {src:'https://previews.123rf.com/images/breadmaker/breadmaker1510/breadmaker151000014/47256597-kitchen-interior-with-two-islands-two-sinks-cabinets-and-hardwood-floors-in-new-luxury-home.jpg', title:'Private room', spaciality:'Cozy, peaceful and private room with...', star:'4.54'},
          {src:'https://cdn.wallpapersafari.com/64/1/XoSwhC.jpg', title:'Entire house', spaciality:'Mordern House in a remote area', star:'4.64'},
         
      ],
       objects:[
          {src:'https://cdn.wallpapersafari.com/64/1/XoSwhC.jpg', title:'Private room', spaciality:'Cozy, peaceful and private room with....', star:'4.64'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21603/stockernumber2160300034/53564553-bedroom-interior-3d-illustration.jpg', title:'Private room', spaciality:'Modern apartment close to nature', star:'4.54'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21702/stockernumber2170200063/70876514-interior-dining-area-3d-illustration.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.85'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21603/stockernumber2160300034/53564553-bedroom-interior-3d-illustration.jpg', title:'Entire house', spaciality:'Mordern House in a remote area', star:'4.96'},
          {src:'https://img5.goodfon.com/wallpaper/nbig/f/f6/interer-pentkhaus-gostinaia-prostranstvo-luxury-penthouse-in.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.40'},
          {src:'https://i.pinimg.com/originals/94/db/d1/94dbd1cb0573dac7bcc1af0f51e2d1ac.jpg', title:'Private room', spaciality:'Cozy, peaceful and private room with...', star:'4.25'},
         
      ],
      
       images:[
          {src:'https://i.pinimg.com/originals/94/db/d1/94dbd1cb0573dac7bcc1af0f51e2d1ac.jpg', title:'Entire house', spaciality:'Mordern House in a remote area', star:'4.64'},
          {src:'https://cdn.wallpapersafari.com/64/1/XoSwhC.jpg', title:'Private room', spaciality:'Cozy, peaceful and private room with...', star:'4.54'},
          {src:'https://i.pinimg.com/originals/94/db/d1/94dbd1cb0573dac7bcc1af0f51e2d1ac.jpg', title:'Entire house', spaciality:'Mordern House in a remote area', star:'4.96'},
          {src:'https://previews.123rf.com/images/stockernumber2/stockernumber21702/stockernumber2170200063/70876514-interior-dining-area-3d-illustration.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.85'},
          {src:'https://img5.goodfon.com/wallpaper/nbig/f/f6/interer-pentkhaus-gostinaia-prostranstvo-luxury-penthouse-in.jpg', title:'Entire apartment. 2 beds', spaciality:'Stylist apartment in center of the city', star:'4.40'},
          {src:'https://i.pinimg.com/originals/94/db/d1/94dbd1cb0573dac7bcc1af0f51e2d1ac.jpg', title:'Private room', spaciality:'Cozy, peaceful and private room with...', star:'4.25'},
         
      ],
    
      
       products:[
            {
            id:1,
            name: 'Adults',
            age:0,
            detail:'Ages 13 or above'          
             
          },
            {
            id:2,
            name: 'Children',
            age:0,
            detail:'Ages 2-12'          
             
          },
     ],
       showCart:false,
        showSearch:false,
        showGuest:false,
        showLocation:false
    };
    
  },
  computed:{
    cart(){
        return this.products.filter(product => product.age >0);
      },

      totalAge(){
        return this.products.reduce(
          (total, product)=> total + product.age,
          0
        );
  },
  filteredPlaces() {
 return this.places.filter(place => place.country.toLowerCase().includes(this.search.toLowerCase()));

      },
  showPlaces(){
    return`${this.filteredplaces.country} ${this.filteredplaces.city}`
  }    

  },
  methods:{


  saveSession(){
    this.loading=!false
    setTimeout(()=>
    {
      this.loading=!true
    },2000)
  },

 updateCart(product, updateType){
          for (let i=0; i<this.products.length; i++){
            if(this.products[i].id===product.id){
              if(updateType==='subtract'){
                if(this.products[i].age !== 0){
                  this.products[i].age--;
                }
              }    else{
                     this.products[i].age++;

              }
              break;
            }
          }
 
 },

},

 showSearch:false,
 showLocation:false
  }
</script>

<style>
.header{
  display:flex;
  justify-content:space-between;
  align-items:center;
  position:sticky;
  z-index:100;
  position:relative;
  width:100%;
  background-color:white;

}
.guest_btn{
  display:flex;
  justify-content:space-between;
  align-items:center;
  position:fixed;
  min-width:70px;
  background-color:white;
  margin-left:24rem;
  margin-top:-5rem;
  border-radius:15px;
  border:1px solid black;

}
.cart-dropdown{
  display:flex;
  flex-direction: column;
  position:absolute;
  margin-top:21rem;
  margin-left:35rem;
  width:370px;
  height:250px;
  background:white;
  border-radius: 15px;
  box-shadow:0px 6px 18px -9px rgba(0, 0, 0, 0.75);
  
}
.header_icon{
  object-fit: contain;
  height:50px;
  margin:20px;
 }

.header_center{
  display:flex;
  flex:1;
  align-items: center;
  max-width:fit-content;
  padding:10px;
  height:40px;
  border:2px solid #d3d3d3;
  border-radius:999px;
}
.header_center > input{
  border-style:none;
  width:200px;

  height:80px;
  outline-width:0;
  font-family: 'Baloo Tammudu 2', cursive;
  background:transparent;
}
.add_guest{
  border:none;
  position:relative;
  width:180px;
  padding:10px;
  outline-width:0;
  height:40px;
  color:teal;
  background:transparent;
  margin-left:-4.7rem;
  margin-top:-2.2rem;
  font-size:13px;
   font-family: 'Baloo Tammudu 2', cursive;

} 
.add-guest:focus:after > .guest{
  opacity: 1;
}


.header_center > .search_btn{
  border:none;
  outline-width:0;
} 
.header_center > span{
  font-weight:bolder;

}
.location{
  border-style:none;
  margin-left:-0.7rem;
  margin-top:-0.1rem;
  height:40px;
  margin-right:1rem;
}
.location:hover{
  background:rgb(241, 239, 239);
}

.guest{
  margin-left:1.2rem; 
  font-size:16px; 
  margin-top:0.1rem;
  color:black; 
  position:absolute;
}

.location:focus-within{
    box-shadow:0px 6px 18px -9px rgba(0, 0, 0, 0.75);
    border:2px solid #d3d3d3;
    border-radius:999px;
    margin-left:-.5rem;
    background:white;
}
.search_list{
background:black;
position:absolute;
display:flex;
width:320px;
margin-top:25rem;
border-radius: 15px;
box-shadow:0px 1px 5px 3px rgba(0, 0, 0, 0.12);
}
.autocom_box :hover{
  background:black;
}
.autocom_box > li:hover{
    color:white;
   line-height:10px;
  background:transparent;

}
.autocom_box > .place:hover{
    color:white; 
}
.search_list .autocom_box{

  padding:0px;
  max-height:280px;
  overflow-y:auto;
  box-shadow:0px 1px 5px 3px rgba(73, 73, 73, 0.12);
  
}
 .autocom_box::-webkit-scrollbar{
  width:8px;
  float:right;
  margin-right:0px;
}
::-webkit-scrollbar-thumb{
  background:linear-gradient(transparent,#00ff6a);
  border-radius:6px;
}
::-webkit-scrollbar-thumb:hover{
  background:linear-gradient(transparent,#ff4800);
}
::-webkit-input-placeholder{
  color:teal;
  
}
.search_list.active .autocom_box{
  
}
.autocom_box > li{
  padding:8px 12px;
  cursor: pointer;
  border-radius: 3px;;
  list-style:none;
  text-align:left;
  font-family:Arial, Helvetica, sans-serif;
  font-weight:bold;
  margin-left:0.1rem;
 
  color:rgb(192, 192, 192);
  font-family: 'Kodchasan', sans-serif;
 

}

.add_guest:focus:after{
  display:none;
}
 .search{
  padding-right:5px;
  padding:20px;
  display:flex;
  align-items: center;
  max-width:fit-content;
   height:30px;
  margin-left:3rem;
  flex:1;
  width:200px;
font-family: 'ABeeZee', sans-serif;
  outline-width:0;
  background-color:rgb(248, 105, 53);
  border:2px solid lightgray;
  border-radius:999px;
  color:white;
  transform:scale(1.07);
  box-shadow:0px 6px 18px -9px rgba(0, 0, 0, 0.75);
}
#icon{
  padding-left:10px;
  float:right;
}


.header_right{
 display:flex;
 align-items:center;
 justify-content:space-between;
 width:15vw;
 margin-right:80px;
}
.header_right{
  font-family: 'Asul', sans-serif;
}
.home_section{
  display:flex;
  padding:30px;
}
.items{
   margin-left:-10rem;
   color:gray;  
 }
 .items h6{
   font-size:20px;
   font-family:'Poppins', sans-serif;
   margin-left:12rem;
   color:rgb(53, 51, 51);
 }
.items p{
  font-size:20px;
  color:black;
  margin-top:-2rem;
  margin-left:12rem;
  font-family: 'Kodchasan', sans-serif;
  font-weight:bold;
}

#number{
padding:5px;
  font-size:16px;
} 
.decrease {
  margin:10px;
  margin-left:rem;
  align-items:center;
  font-size:24px;
  color:rgb(94, 93, 93);
  border-radius:50%;
  background:transparent;
  width:35px;
  height:35px;
  border:1px solid gray;
    outline-width:0;
  
}
.close_btn{
  display:flex;
  justify-content:space-between;
  align-items:center;
  position:fixed;
  min-width:50px;
  margin-left:21rem;
  margin-top:-0.5rem;
 
}
.close{
  margin-top:1rem;
  margin:10px;
  align-items:center;
  font-size:24px;
  background:transparent;
  outline-width:0;
  border-style: none;
  
  }
#close{
  padding-top:-1rem;
  font-size:14px;
  color:gray;
}

.close:hover{
  width:30px;
  height:30px;
  border-radius: 50%;
  background-color: rgb(175, 173, 173);
}
.close:hover > #close{
  color:black;
}

.increase{
  margin:10px;
  outline-width:0;
  font-size:24px;
  color:rgb(78, 78, 78);
  width:35px;
  height:35px;
  background:transparent;
  border:1px solid gray;
  border-radius:50%;
}
.dropdown_list{
   list-style: none;
   position:absolute;
   
  }
 
li{
  color:black;
  margin-left:-2rem;
 text-align:left;
 
 
}
</style>