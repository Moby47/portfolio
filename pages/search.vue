<template>
    <div>
        
        
        <div class="body-back">
            <div class="masthead pdng-stn1">
        
                <div class="phone-box wrap push" id="home">
                    <!-- /banner -->
                    <div class="banner_inn_sec elevation-16">
                    </div>
                    <!-- //banner -->
    
                    <!--/blog-->
                    <div class="services-section">
                        <div class="wrap_view_agileits">
                            <h3 class="head">Result(s)</h3>
                                      
                            <div class="inner_section_wthree">
    
            
                                <!-- ********************************************** blog -->
                                
                                <div class="col-md-7 blog_section">
                                    
                                        <div v-if='empty' class='text-center alert alert-info'>
                            No blog post found...... <nuxt-link to='/'>GO HOME</nuxt-link>
                                                </div>
                        
                                                 <!--loading temp-->
                     <transition name='anime' enter-active-class='animated fadeIn' :duration='200' leave-active-class='animated fadeOut'>
                    <div v-if='data_load' class='text-center'>
                      <template>
                            Loading Posts...
                         <v-progress-circular indeterminate></v-progress-circular>
                                </template>
                                 </div>
                        </transition>
                                                          <!--loading temp-->
    
    
                             <!--loading temp-->
     <transition name='anime' enter-active-class='animated fadeIn' :duration='200' leave-active-class='animated fadeOut'>
                                    <div v-if='wait'>
                                      <template>
                                        Please stand by...
                                         <v-progress-circular indeterminate></v-progress-circular>
                                                </template>
                                                 </div>
                                        </transition>
                              <!--loading temp-->
    
                      <transition name='anime' enter-active-class='animated fadeIn'leave-active-class='animated fadeOut'>
                      <span v-if='data'>
                <div class="blog_img">
                        <div v-for='con in content' v-bind:key='con.id' class='elevation-10 wow slideUp blog_con text-capitalize'>
                                <nuxt-link :to="'blog/'+con.title.replace(/[.,/*%' '?!#:;{}$%+=`()@]/g,'-')+'/'+con.id">
                                    <v-img
                                       class="white--text mobile-size"
                                       height="300px"
                                       :src="'http://localhost:8000/storage/blog/'+con.image"
                                        :alt="con.title"
                                        :lazy-src="`http://localhost:8000/images/black-spinner.gif`"
                                     >
                                     </v-img></nuxt-link>
                                <div class="col-md-2 blog_date">
                                    <h4> <span> {{moment(con.created_at).fromNow()}}</span></h4>
                                </div>
                                <div class="col-md-6 blog_info">
            
                                    <p><nuxt-link :to="'blog/'+con.title.replace(/[.,/*%' '?!#{}$%+=`:;()@]/g,'-')+'/'+con.id">
                                        <h5>{{con.title}} 	</h5>
                                        </nuxt-link></p>
            
                                    <ul class="blog_list">
                                        <li><span class="fa fa-list" aria-hidden="true"></span>{{con.category}}<i>|</i></li>
                                        <li><a href="" @click.prevent='like(con.id)'><span class="fa fa-thumbs-up" aria-hidden="true"></span></a></li>
                                    </ul>
            
                                </div>
                                <div class="clearfix"> </div>
                                <p>
                                {{con.description.substr(0,80)}}...
                                <nuxt-link :to="'blog/'+con.title.replace(/[.,/*%' '?!#{}$%+=`:;()@]/g,'-')+'/'+con.id">
                                More
                                </nuxt-link>
                                </p>
                            </div>
    
    
                </div>
                                    <div class='text-center' v-if='!empty'>
                                    <div class="pagination ">
                                            <button class='btn btn-primary custombtn' @click.prevent="fetch(pagination.prev_page_url)" :disabled="!pagination.prev_page_url">
                                            Prev
                                            </button>
                                                                            
                                            <span>Page {{pagination.current_page}} of {{pagination.last_page}}</span>
                                                                            
                                            <button class='btn btn-primary custombtn' @click.prevent="fetch(pagination.next_page_url)" :disabled="!pagination.next_page_url">
                                             Next
                                            </button>
                                            </div> 
                                        </div> 
                    </span>
                </transition>
                                            
                                </div>
                
                                <!-- ********************************************** blog -->
    
                                <div class="col-md-5 blog_left ">
                                    <div class="search left_bar">
                                            <h3>Search </h3>
                                                <form action="#" method="post">
                                                    <input class="email" v-model='query' v-validate='"required"' type="email" name="Search" placeholder="Eg: PWA" >
                                                    <input type="submit" @click.prevent='search()' value="Search" class='text-white'>
                                                    
                                                </form> 
                                            <br>
                                                
                                        <h3>Subscribe </h3>
                                        <form action="#" method="post" data-vv-scope='subscribe'>
                                            <input class="email" v-model='Email' v-validate='"required|email"' type="email" name="Email" placeholder="Email here" >
                                                                                <input type="submit" @click.prevent='sub()' value="Send" class='text-white'>
                                                                                <transition name="fadeLeft">
                                                        <span class='custom-alert' v-show="errors.has('subscribe.Email')">{{ errors.first('subscribe.Email') }}</span>
                                                                                       </transition> 
                                                                            </form>
                                    </div>
                                    <div class="author left_bar">
                                        <h3>About <span>Admin</span></h3>
                                        <div class="author_grid">
                                            <p>Henry Onyemaobi is a goal driven, self taught, fullstack web developer. 
                                                Fueled by enthusiasm for computing.</p>
                                            <div class="author_grid_pos">
                                                <img src="http://localhost:8000/images/Henry onyemaobi web developer.jpg" 
                                                alt="Henry onyemaobi web developer in lagos state" 
                                                class="img-responsive">
                                            </div>
                                        </div>
                                    </div>
    
                                    <div class="categories left_bar">
                                        <h3>Categories</h3>
                                        <ul>
                                            <li><nuxt-link to="/category/all"><span class="fa fa-angle-right" aria-hidden="true"></span>All categories</nuxt-link></li>
                                            <li><nuxt-link to="/category/fixes"><span class="fa fa-angle-right" aria-hidden="true"></span>Bug fixes</nuxt-link></li>
                                            <li><nuxt-link to="/category/how-to"><span class="fa fa-angle-right" aria-hidden="true"></span>How to</nuxt-link></li>
                                            <li><nuxt-link to="/category/installations"><span class="fa fa-angle-right" aria-hidden="true"></span>Installations</nuxt-link></li>
                                            <li><nuxt-link to="/category/others"><span class="fa fa-angle-right" aria-hidden="true"></span>Others</nuxt-link></li>
    
                                        </ul>
                                    </div>
                                </div>
                                <div class="clearfix"> </div>
                            </div>
                        </div>
                    </div>
                    <!--//blog-->
    
                <!--//footer-->
                    
                    <!--//footer-->
    
                </div>
            </div>
        </div>
    
        
    </div>
    </template>
    
    <style scoped>
        .theme--light.v-sheet{
            margin-bottom: 20px;
        }
     
.custombtn{
  background-color: #123c69 !important;
  color:white;
}
        .fa-heart{
            color:red;
        }
    </style>
    
    <script>

        import axios from 'axios'
    
    var moment =require('moment');
    
      export default {
        data () {
          return {
            moment:moment,
            page: 1,
            Email:'',
            load:'',
            content: [],
            pagination: [],
            loading: false,
            data_load: true,
            data: false,
            valerror:[],
            empty: false,
            wait: false,
    
            query:'',
          }
        },
        
        methods: {
    
            search(){
                this.$nuxt.$loading.start()
                if(this.query == ''){
                    alert("Please enter a word.");
                }else{
                   
                    var   page_url = page_url || 'http://localhost:8000/search-blog/'+this.query;
    
              fetch(page_url)
              .then(res => res.json())
              .then(res=>{
                this.content = res.data;
                //to determine if obj is empty 
                        //console.log(res.data[0]);
                        if(res.data[0] == undefined){
                            this.empty = true;
                        }else{
                            this.empty = false;
                        }
                //to determine if obj is empty
                this.makePagination(res.meta, res.links);
                this.wait = false;
                this.$nuxt.$loading.finish();
              })
              .catch(error =>{
                  console.log(error)
                  //off loader
                  this.data_load = false;
                    this.wait = true;
                 /*   setTimeout(func=>{
                        this.fetch();
                    },2000)
                    */
                    this.$nuxt.$loading.finish();        
                  })
                }
                this.$nuxt.$loading.finish()
            },
    
            sub(){
      //validate
  this.$validator.validateAll('subscribe').then(() => {
       
  if (!this.errors.any()) {
         //if no error
         //NProgress.start()
        // instantiant formdata object
   const formdata  = new FormData();
//append form data to formdata
formdata.append('Email', this.Email);

//send to database with axios
    axios.post('http://localhost:8000/api/subscribe',formdata
).then(res=>{
if(res.data == 1){
alert("Thank you! For Subscribing.");

}else if(res.data == 'exist'){
alert("Email exists in our records, Thank you!");

//clear form and errorbag
this.Email ='';
setTimeout(func=>{
    this.errors.clear()
},100) 
//clear form and errorbag
}else{
alert("An Error Occured, Please contact Admin");
}
//NProgress.done()
})
.catch(error =>{
              if(error.response.status == 422){
                this.valerror = error.response.data.errors;
                if(this.valerror){
                  alert("Please verify your email is correct...");
                }
              }
        ////NProgress.done();        
          })

 }else{
   //error occured

 }

}); //validator
    },
    
    
            //fetch blogs
     fetch(page_url){
                if(page_url){
                this.$nuxt.$loading.start();
                }
                //off snackbar
                this.snackbar = false;
              var   page_url = page_url || 'http://localhost:8000/search-blog/'+this.$route.params.query;
    
              fetch(page_url)
              .then(res => res.json())
              .then(res=>{
                this.content = res.data;
                //to determine if obj is empty 
                        //console.log(res.data[0]);
                        if(res.data[0] == undefined){
                            this.empty = true;
                        }else{
                            this.empty = false;
                        }
                //to determine if obj is empty
                this.makePagination(res.meta, res.links);
                this.wait = false;
                this.$nuxt.$loading.finish();
              })
              .catch(error =>{
                  console.log(error)
                  //off loader
                  this.data_load = false;
                    this.wait = true;
                 /*   setTimeout(func=>{
                        this.fetch();
                    },2000)
                    */
                    this.$nuxt.$loading.finish();        
                  })
                  
             
            },
    
             makePagination(meta, links){
        var pagination = {
                        current_page: meta.current_page,
                        last_page: meta.last_page,
                        next_page_url: links.next,
                        prev_page_url: links.prev
                         }
                                             document.body.scrollTop = 0;
            document.documentElement.scrollTop = 0;
        this.pagination = pagination;
            },
            
            like(id){
                
                this.loading = true;
                var check = localStorage.getItem('userId');
                if(check){
                    this.$nuxt.$loading.start()
                    //Id exists, send both User and Post Id to DB
                    var userId = check;
                    var postId = id;
    
                    var input = {'userId':userId, 'postId':postId};
    
                    axios.post('http://localhost:8000/api/like',input)
                    .then(res=>{
                        if(res.data == 1){
                    alert('Post Liked!');
                    //this.fetch();
                        }else if(res.data == 0){
                    alert('You Liked This Post Already...');
                    //clear in 3 secs
                setTimeout(func=>{
                
                },3000)
                        }
                        this.$nuxt.$loading.finish();
                        this.loading = false;
                    })
                    .catch(error =>{
              alert("The like action failed...");
              this.loading = false;
                this.$nuxt.$loading.finish();        
                  })
                    
                }else{
                    this.$nuxt.$loading.start();
                    //create id for user  
                var userId = Math.floor(Math.random()*1000);
                //store locally
                localStorage.setItem('userId',userId);
                var postId = id;
    
                //go to server
                var input = {'userId':userId, 'postId':postId};
                axios.post('http://localhost:8000/api/like',input)
                    .then(res=>{
                        if(res.data == 1){
                    alert('Post Liked!');
                    //clear in 3 secs
                setTimeout(func=>{
                
                },3000)
                        }
                        this.$nuxt.$loading.finish();
                        this.loading = false;
                    })
                    .catch(error =>{
              alert("The like action failed...");
              this.loading = false;
                this.$nuxt.$loading.finish();        
                  })
                }
                
                
            },
    
        },
    
        //watch data load
    watch : {
          content(a,b){
           if(a){
            //data content loaded, it is safe to display
            this.data_load = false;
            this.data = true;
           }
        },
         //watch for url param changes, meaning user SEARCHED AGAIN
         $route (to,from){
                
                this.fetch();
            }
    },
    
        mounted(){
                
                this.fetch();
            }
      }
    </script>