!<template>
<div class="allHeader">


   <!-- <slot name="sideBar" class="sideBarButton">


   </slot> -->

      <router-link to="/modeSelection">
          <img class="headerTilte" v-lazy="'/static/banvasLogo.png'" alt="headerTitle">
        
      </router-link>

          <router-link to="/modeSelection">
         <span class="headerText">Banvas Au</span>

            </router-link>

      <slot name="search" class="searchBar">
          


      </slot>
   
        <a-menu
              theme="light"
              mode="horizontal"
              style="{lineHeight: 64px}"
              class="userInfoSlot"
            >
                <a-sub-menu >
                    <span slot="title" 
                    >
                    <img alt="" v-lazy="'/static/endUser.png'" style="height: 2vw;  width: auto; borderRadius: 50%; marginRight: 0.5vw" v-if="!hasPhoto|| !photoCorrect"/>
                      <img alt="" v-lazy="this.photo" style="height: 2vw;  width: auto; borderRadius: 50%; marginRight: 0.5vw" v-if="hasPhoto&photoCorrect"/>
                    <span style="fontSize: 1.3vw; marginTop: 0.5vh">{{username}}</span>
                    </span>

                    <a-menu-item key="setting:1">
                       <router-link to="/profile"/>
                        Profile
                      </a-menu-item>

                      <a-menu-item key="setting:2" @click="logout">
                        Login Out
                      </a-menu-item>
              
          
                </a-sub-menu>
            
            </a-menu>
      
      
</div>
  
</template>

<script>
 import userService from '../services/userService'
 import "../assets/css/header.css";
  export default {

    data(){
       return {
          username: "Mark",
          photo: "",
          hasPhoto: false,
          photoCorrect: false
       }

    }, 
    components:{
      userService
    },

    created(){
      
       
    },

    
    mounted(){
      
           
        const userid = this.$cookies.get('userid')
        if(userid){
              userService.getUserInfo(userid).then(user=>{
                   
                 if(user.data[0].photo || user.data[0].lastname){
                     console.log(user)
                    this.username = user.data[0].lastname
                    this.photo = user.data[0].photo
                    this.hasPhoto = true
                    this.checkPhoto()
                    this.$emit('currentUser',user.data[0])
                 }
        });
        
        }else{
            alert('please login first')
            this.$router.push({path: "/login"})

      }


    },

    methods:{
        onChange(checked) {
      // console.log(`a-switch to ${checked}`);
    },

    checkPhoto(){
   
      if(this.photo.includes('base64')){
          
          this.photoCorrect = true
      }


    },

    async logout(){
       const userid = this.$cookies.get('userid')
      let confirmation = confirm('Are you sure log out?') 
             if(confirmation){
                this.$cookies.remove("firstname"); 
                this.$cookies.remove("lastname");
                this.$cookies.remove("state");
                this.$cookies.remove("username");
                this.$cookies.remove("userid");
                this.$router.push({path:"/login"})
            }
       }

    }
  }
</script>

<style lang="less" scoped>

.allHeader{
  height: 53px;
  padding: 0;
  line-height: 4.5vh;
  width: 100%;
  background: white;
  overflow: hidden;
  text-align: center;
  border-bottom: 1px solid #dbdbdb;  
  border-top:0px;  
  border-left:0px;  
  border-right:0px;  
  display: grid;
  grid-template-columns:  3% 22% 50% 25%; 
  grid-template-rows: 100%;
}

/deep/ .ant-layout-header{
  height: 53px;
  padding: 0;
  line-height: 64px;
  width: 100vw;
  background: white;
  overflow: hidden;
  border-radius: 5px;
   -webkit-box-shadow: #666 0px 0px 10px;
  -moz-box-shadow: #666 0px 0px 10px;
  box-shadow: #666 0px 0px 10px;

  }

  .headerText{
     font-size: 2vw;
     font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
     color: black;
     margin-top:0.1vh;
     margin-right: 3vw;
     grid-column: 3;
     grid-row: 1;
     float: left;

  }

.userInfoSlot{
  position: relative;
  left: 8vw;
  top: 0.1vh;
  // float:right;
  grid-column: 4;
  grid-row: 1;
}

.searchBar{
  grid-column: 3;
  grid-row: 1;
}

/deep/ .ant-menu-submenu{
   border-bottom: 0 !important; 
  
}

.sideBarButton{
   text-align: center;
   grid-column: 1;
   grid-row: 1;
}

</style>