<template>
    <div>
        我是详情页{{this.$route.id}}
    </div>
</template>
<script>
export default {
    data(){
        return{

        }
     
    },
    watch:{
        $route(to, from) {  
                console.log(to);  
                console.log(from);  
            } 
    }

}
</script>
