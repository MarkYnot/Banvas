!<template>
   <div>
      <a-menu
      :default-selected-keys="['1']"
      :default-open-keys="['sub1']"
      mode="inline"
      theme="light"
      :inline-collapsed="collapsed"
    >
      <a-menu-item key="1">
            <router-link to="/modeSelection"/>
            <a-icon type="home" />
            <span>Home</span>
      </a-menu-item>


      <a-menu-item key="2">
          <router-link to="/video/collection"/>
          <a-icon type="save" theme="filled"/>
          <span>Save List</span>
      </a-menu-item>


      <a-menu-item key="3">
            <router-link to="/video/likes"/>
          <a-icon type="like" theme="filled"/>
          <span>Like videos</span>
      </a-menu-item>

        <a-menu-item key="4">
            <router-link to="/videoCentre"/>
          <a-icon type="video-camera" />
          <span>Video Centre</span>
        </a-menu-item>

        
        <a-menu-item key="5">
            <router-link to="/profile"/>
          <a-icon type="setting" theme="filled"/>
          <span>Profile</span>
        </a-menu-item>

         <a-menu-item key="6">
            <router-link to="/changePassword"/>
          <a-icon type="inbox" />
          <span>Change Password</span>
        </a-menu-item>
      
             <a-menu-item key="7">
            <router-link to="/video&1"/>
          <a-icon type="video-camera" />
          <span>Recommanded Video</span>
        </a-menu-item>

            <a-menu-item key="8">
            <router-link to="/game1"/>
          <a-icon type="play-circle" />
          <span>Recommanded Game</span>
        </a-menu-item>
    
   </a-menu>


  </div>
</template>

<script>
  export default {
    props:{
        collapsed:{
           type:Boolean
        }
    }
    
  }
</script>

<style lang="less" scoped>
// .sideBar{
//   grid-row: 1;
//   grid-column: 1;
// }

/deep/ .ant-menu-item-selected{
  color: black;
}

/deep/ .ant-menu:not(.ant-menu-horizontal) .ant-menu-item-selected {
    background: #dbdbdbb6;
}

/deep/ .ant-menu-inline .ant-menu-item::after{
   border-right: 0px;
}

/deep/ .ant-menu-item:hover{
    color:black;
}

/deep/ .ant-menu-submenu-title:hover{
     color:black;
}

/deep/ .ant-menu-submenu-inline > .ant-menu-submenu-title:hover .ant-menu-submenu-arrow::before{
     background:linear-gradient(to right, black, black);
}

/deep/ .ant-menu-item span {
      font-size: 1.1vw;
      font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif
}

/deep/ .ant-menu-submenu-title span{
    font-size: 1.1vw;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif
}

/deep/ .ant-menu-inline .ant-menu-item {
        font-size: 0.8vw;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

/deep/ .ant-menu i{
  float: left;
  margin-top: 0.6vh;
}

/deep/ .ant-menu span{
  float: left;
}

/deep/ .ant-menu-item .anticon, .ant-menu-submenu-title .anticon{
  font-size:1.1vw;
}

/deep/ .ant-menu-inline .ant-menu-item:not(:last-child){
  margin-bottom: 15px;
}

/deep/ .ant-menu .ant-menu-inline .ant-menu-sub .ant-menu-item{
    padding-left: 0px;
    
}

/deep/ .ant-menu-submenu-selected {
  color: black;
}
</style>