<template>
<div>
    <page-header></page-header>
    <div class="main-container" :style="{height:height + 'px'}">
        <page-side :isCollapse="$store.getters.sidebar"></page-side>
        <div class="main-content" :class="{'is-collapse':$store.getters.sidebar}">
            <router-view />
        </div>
    </div>
</div>
</template>

<script>
import PageHeader from './PageHeader'
import PageSide from './PageSide'
export default{
    components:{
        PageHeader,
        PageSide
    },
    data(){
        return{
            height:0
        }
    },
    mounted(){
        this.$nextTick(()=>{
            this.height = window.innerHeight - 61
        })
    }
}
</script>

<style scoped>
.main-container{
    width:100%;
}
.main-content{
    display:inline-block;
    vertical-align:top;
    width:calc(100% - 166px);
    height:100%;
    overflow:auto;
    min-width:794px;
}
.main-content.is-collapse{
    width:calc(100% - 66px);
}
.main-content>div{
    margin:15px;
}

.main-content::-webkit-scrollbar{
    display:none;
}

@media (max-width:960px){
    .main-container{
        width:960px;
    }
}
</style>