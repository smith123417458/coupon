<template>
    <div class="allsideBar">
        <div class="sidebarAdmin bigSizeUse">
            <span>管理列表</span>
            <ul class="sidebar_ul">
                <li class="sidebar_li">
                    <router-link to="/admin/products">   
                        產品列表
                    </router-link>
                </li>
                <li class="sidebar_li">
                    <router-link to="/admin/coupons">
                        優惠券列表
                    </router-link>
                </li>
                <li class="sidebar_li">
                    <router-link to="/admin/orders">
                        訂單列表
                    </router-link>
                </li>
            </ul>
        </div>       
    </div>
</template>

<script>



export default {
  name: 'Sidebar',
  data(){
    return{
      show: true,
    }
  }
}
</script>

<style>
    .ul-enter-active,.ul-leave-active {
        transition: all 0.5s;
    }
    .ul-enter,.ul-leave-to {
        height: 0;
    }
</style>