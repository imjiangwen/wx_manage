<template>
    <el-select v-model="selectedAppid" size="small" v-loading="dataListLoading"  @change="selectAccount" filterable>
        <el-option v-for="item in accountList" :key="item.appid" :label="item.name" :value="item.appid"></el-option>
    </el-select>
</template>
<script>
import { mapState } from 'vuex'
export default {
    data() {
        return {
            dataListLoading: false,
            accountList: [],
            selectedAppid : ''
        }
    },
    mounted(){
        this.getDataList()
    },
    methods:{
        getDataList() {
           this.accountList = [{appid:'wx48f18d972459336a',name:'测试'}];
        },
        selectAccount(appid){
            if(this.selectedAppid!=appid){
                this.selectedAppid = appid
            }
        }
    }
}
</script>