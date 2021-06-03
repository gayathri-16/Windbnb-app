<template>
    <div id="content">
         <div class="card" v-for="detail in details" :key="detail">
             <img style="" class="card_image" :src="detail.src" alt="" >
                  <div class="card_info">
                     <button class="btn">Super host</button>  <h5>{{detail.title}}
                       <span><i class="fas fa-star" style="margin-right:5px;color:red;"></i>{{detail.star}}</span></h5>
                       <h2> {{detail.spaciality}} </h2>
                   </div> 
         </div>
          <div class="card" v-for="object in objects" :key="object">
             <img style="" class="card_image" :src="object.src" alt="" >
                  <div class="card_info">
                       <h4>{{object.title}}
                       <span><i class="fas fa-star" style="margin-right:5px;color:red;"></i>{{object.star}}</span></h4>
                       <h2> {{object.spaciality}} </h2>
                   </div>
         </div>
          <div class="card" v-for="image in images" :key="image">
             <img style="" class="card_image" :src="image.src" alt="" >
                  <div class="card_info">
                       <h4>{{image.title}}
                       <span><i class="fas fa-star" style="margin-right:5px;color:red;"></i>{{image.star}}</span></h4>
                       <h2> {{image.spaciality}} </h2>
                   </div>
         </div>
  
       
   </div>
</template>

<script>
    export default {
       props:['details','objects','images'],
        
    }
</script>

<style>
#content{
    margin-top:4rem;
}
.card{
    margin:20px;
    border-radius: 10px;
    box-shadow:0px 6px 18px -9px rgba(0, 0, 0, 0.75);
    transition:transform 100ms ease-in;
    cursor:pointer;
    min-width:100px;
    min-height:100px;
    margin-top:5rem;
    
}
.card:hover{
    transform:scale(1.07);
}
.card > img{
    min-width:100px; 
    min-height:100px;
    object-fit: contain;
    width:100%;
    height:100%;
    display:flex;
    border-radius:10px;
}
.card_info{
    border-radius:10px;
    padding: 10px;
    padding-top:1px;
    border:1;
}
.card_info > h5{
    font-size:16px;
    color:gray;
    font-family:'Ubuntu', sans-serif;
    font-weight:lighter;
    margin-left:7.5rem; 
    margin-top:-1.3rem;   
    margin-right:1rem;

}
.card_info > h4{
    font-size:16px;
    color:gray;
    font-family:'Ubuntu', sans-serif;
    font-weight:lighter;
    margin-top:2.2rem;
    

}
.card_info > h2{
    color:rgb(39, 38, 38);
    font-size:25px;
    font-family: 'Tenali Ramakrishna', sans-serif;
    margin-top:1rem;
}
.card_info > .btn{
    width:110px;
    height:30px;
    border-radius:15px;
    font-size:12px;
    border:1px solid gray;
    margin-top:1rem;
    font-weight:bolder;
    text-transform: uppercase;
    outline-width:0;
}
span{
  float:right;
  }

</style>
 