<template>
    <div id="addAddress">
        <van-nav-bar
            title="添加地址"
            left-arrow
            :fixed=true
            :border=true
            @click-left="onClickLeft"
        ></van-nav-bar>
        <van-address-edit
            :area-list="areaList"
            show-postal
            show-set-default
            show-search-result
            :search-result="searchResult"
            :area-columns-placeholder="['请选择', '请选择', '请选择']"
            @save="onSave"
            @change-detail="onChangeDetail"
            style="margin-top: 3rem;"
        ></van-address-edit>

    </div>
</template>

<script>
    import { Toast } from 'vant';
    export default {
        name: "AddAddress",
        data() {
            return {
                areaList:{},
                searchResult: []
            }
        },
        methods:{
            //点击了左边
            onClickLeft(){
                this.$router.go(-1);
            },
            onSave() {
                Toast('save');
            },
            onChangeDetail(val) {
                if (val) {
                    this.searchResult = [{
                        name: '黄龙万科中心',
                        address: '杭州市西湖区'
                    }];
                } else {
                    this.searchResult = [];
                }
            }
        }
    }
</script>

<style scoped>
    #addAddress{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: #f5f5f5;
        z-index: 9999;
    }
</style>
