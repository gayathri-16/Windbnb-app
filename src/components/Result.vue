<template>
    <div>
        <link href="https://fonts.googleapis.com/css2?family=Courgette&family=El+Messiri&family=Lemonada:wght@300&family=New+Rocker&family=Original+Surfer&display=swap" rel="stylesheet">
    <div class="searchResult">
        <img :src="image" alt="">
        <i class="fas fa-heart" id="searchResult_heart"></i>
        <div class="searchResult_info"> 
        <div class="searchResult_infoTop">
            <p> {{location}} </p>
            <h3> {{title}} </h3>
            <p>_____</p>
            <p> {{description}} </p>
        </div>
    
         <div class="searchresult__infoBottom">
             <div class="searchResult__star">
                 <i class="fas fa-star" style="color:red;"></i>
                 <p><strong> {{star}} </strong></p>
             </div>
             <div class="searchResult__price">
                 <h2> {{price}} </h2>
                 <p> {{total}} </p>
             </div>
         </div>

        
       </div>
    </div>
</div>
</template>

<script>
    export default {
        props:['image','location','title', 'description','star','price','total']
    }
</script>

<style>
.searchResult{
    display:flex;
    position:relative;
    margin:20px;
    padding:20px;
    border-bottom:1px solid lightgray;
  
    cursor:pointer;

}
.searchResult:hover{
    opacity:0.8;
}
.searchResult > img {
    height:200px;
    width:350px;
    border-radius:10px;
    overflow:hidden;
}
.searchResult_info{
    display:flex;
    flex-direction: column;
    justify-content: space-between;
    padding-left:20px;
}
#searchResult_heart{
    position:absolute;
    top:20px;
    right:40px;

}
.searchResult_infoTop{
    width:40vw;
}
.searchResult_infoTop > h3{
    font-weight:300;
    margin-top:10px;
    font-family: 'New Rocker', cursive;
}
.searchResult_infoTop > p{
    font-size:13px;
    margin-top:10px;
    color:gray;
    font-family: 'Lemonada', cursive;
}
.searchResult_infoBottom{
    display: flex;
     justify-content: space-between;

}
.searchResult__star{
    display: flex;
    align-items: center;
}
.searchResult__price > p{
    text-align:right;

}
.searchResult__price{
    position:absolute;
    bottom:20px;
    right:30px;
}
.searchpage_info{
    padding:20px;
}
.searchpage_info>p{
    margin-bottom:10px;
    font-size: 14px;
}
.searchpage_info>p{
    margin-bottom:30px;
}
.searchpage_info > button{
    border-radius:20px;
    text-transform:inherit;
    margin:5px;
    outline:none;
    padding: 8px;
    font-size:14px;
    border:1px solid gray;
}
</style>