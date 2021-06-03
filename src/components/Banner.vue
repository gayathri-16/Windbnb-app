<template>
    <div>
        <link href="https://fonts.googleapis.com/css2?family=Courgette&family=El+Messiri&family=Original+Surfer&display=swap" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css2?family=El+Messiri&family=Original+Surfer&display=swap" rel="stylesheet">
        <link href="https://fonts.googleapis.com/css2?family=Courgette&family=El+Messiri&family=New+Rocker&family=Original+Surfer&display=swap" rel="stylesheet">
         <link href="https://fonts.googleapis.com/css2?family=Courgette&family=El+Messiri&family=Montserrat+Alternates:wght@100&family=New+Rocker&family=Original+Surfer&display=swap" rel="stylesheet">
      <div class="banner">
            <div class="banner_search">
                <button variant='outlined' class="banner_searchButton">Search Dates</button>
            </div>

            <div class="banner_info">
                <h1>Get out and stretch your imagination</h1>
                  <h5>
                      Plan a different kind of 
                      gateaway to uncover the hidden 
                      gems near you. 
                  </h5>
        
           
                  <button><a href="#search_page">EXPLORE NEARBY</a></button> 
      
            </div>

      
    </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style>
.banner{
    position:relative; 
    background:url("https://getwallpapers.com/wallpaper/full/c/7/8/1295363-vertical-room-desktop-wallpaper-1920x1200-meizu.jpg") center center;
    height:60vh;
    }
    .banner_info{
        background-color:black;
        color:white;
        padding-top:25vh;
        padding-left:50px;
        padding-right:50px;
        padding-bottom:40px;
        width:300px;
        font-family: 'El Messiri', sans-serif;
        letter-spacing: 1px;
        
    }
    .banner_info > button  {
        background-color:#ff7779;
        color:white;
        text-transform:inherit;
        margin-top:20px;
        font-weight:600;
        padding:10px;
        border-style:none;
        border-radius:4px;
        width:150px;
        text-decoration:none
    }
 a{
        color:white;
        text-decoration: none;
        
        
    }
        a:hover{
            color:#ff7779;
       }
   
    .banner_info >  button:hover{
        background-color:white;
         color:#ff7779;
        
    }
    .banner_info > h5{
        margin-top:10px;
        letter-spacing: 2px;
        font-family: 'Montserrat Alternates', sans-serif;
       
    }
    .banner_search{
        display:flex;
        flex-direction:column;
    }
    .banner_searchButton{
        background-color:white;
        font-weight:900;
        text-transform: inherit;
        color:#ff7779;
        border-style:none;
        border-radius:4px;
        padding:10px;
        outline-width:0;
    }
</style>