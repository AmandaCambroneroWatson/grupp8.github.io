<template>
  <div class="toggle-wraper">
    <label class="toggle">
        <input type="checkbox" 
            :checked="(mode === 'dark') ?'checked' :false"
             @change="$emit('toggle')"/>
        <span class="toggler round"></span> 
        </label>  
  </div>
</template>

<script>
export default {
    props:['mode']

}
</script>

<style>
.toggle{
    
    position: relative;
    display:inline-block;
    width: 50px;
    height: 22px;
    
    
}

.toggle input {
    
    opacity: 0;
    width: 0;
    height: 0; 
}

.toggler{
    position: absolute;
    cursor:pointer;
    top:0;
    left:0;
    right:0;
    bottom:0;
    background:#F0F0F0;
    -webkit-transition: 0.4s;
    transition: 0.4s;
   
}


.toggler:before{
    position: absolute;
    content:"" ;
    height: 21px;
    width: 21px;
    left:2px;
    right:0;
    background:#BDBDBD;
    -webkit-transition: 0.4s;
    transition: 0.4s;
}
input:checked + .toggler{
    background:#5DB075 ;
}
input:focus + toggler {
    box-shadow: 0 0 2px #5DB075 ;
}

input:checked + .toggler:before{
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
}

.toggler.round{
    border-radius: 34px;
    

}

.toggler.round:before{
    border-radius: 50%;
}

</style>