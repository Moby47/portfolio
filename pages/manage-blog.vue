<template>

    <div class="body-back">
        <div class="masthead pdng-stn1">
          
          <div class="phone-box wrap push" id="home">
          

             <!--stat-->
             <template>
                    <div class="text-xs-center">

                      <v-badge left>
                        <template v-slot:badge>
                          <span class='badge'>{{projectct}}</span>
                        </template>
                        <v-icon
                          large
                          color="grey lighten-1"
                        >
                          archive
                        </v-icon>
                        <span v-if='stat_load.proj'><i class=''>Loading..</i></span> 
                      <span v-else> Projects </span> 
                      </v-badge>
                  

                      
                      <v-badge color="red">
                        <template v-slot:badge>
                          <span class='badge'>{{blogct}}</span>
                        </template>
                        <v-icon
                          large
                          color="grey"
                        >
                         comment
                        </v-icon> 
                        <span v-if='stat_load.blog'><i class=''>Loading..</i></span> 
                        <span v-else>  Posts </span>
                      </v-badge>



                      <v-badge color="red">
                            <template v-slot:badge>
                              <span class='badge'>{{subct}}</span>
                            </template>
                            <v-icon
                              large
                              color="grey"
                            >
                              account_circle
                            </v-icon>
                            <span v-if='stat_load.sub'><i class=''>Loading..</i></span> 
                            <span v-else> Subscribers</span>
                          </v-badge>


                          <v-badge color="red" >
                                <template v-slot:badge>
                                  <span class='badge'>{{conct}}</span>
                                </template>
                                <v-icon
                                  large
                                  color="grey"
                                >
                                settings_phone
                                </v-icon>
                                <span v-if='stat_load.con'><i class=''>Loading..</i></span> 
                              <span v-else>  Contacts </span>
                              </v-badge>
                    </div>
                  </template>
            <!--stat-->
           
            <!--/blog-->
            <div class="services-section">
              <div class="wrap_view_agileits">
                <div class="inner_section_wthree">

                  <!--loading temp-->
<div v-if='load'>
    <template>
      <v-progress-linear indeterminate></v-progress-linear>
      </template>
    </div>
    <!--loading temp-->
    
                  <div class="col-md-6 contact_grid_right">
                    <h6>{{title}}</h6>
                    <form action="#" method="post">
                      <div class="col-md-6 col-sm-6 contact_left_grid">
       <input type="text" v-model='Title' v-validate='"required|max:49"' name="Title" placeholder="Title" required="">
       <transition name="fadeLeft">
          <span class='custom-alert' v-show="errors.has('Title')">{{ errors.first('Title') }}</span>
         </transition>                  
      </div>
                      <div class="col-md-6 col-sm-6 contact_left_grid">
        <input type="file" @change='ImageSelect' v-validate='"required|image"' name="Image" placeholder="image" required="" class='custom top'>
        <transition name="fadeLeft">
            <span class='custom-alert' v-show="errors.has('Image')">{{ errors.first('Image') }}</span>
           </transition>                
      </div>
                      <div class="col-md-12 col-sm-12 contact_left_grid">
                          <br>
                          <select class='custom' v-model='Category' v-validate='"required"' name='Category'>
                              <option value="">- Choose Cateogry -</option>
                              <option value="Installations">Installations</option>
                              <option value="Fixes">Fixes</option>
                              <option value="How-to">How to</option>
                              <option value="Others">Others</option>
                            </select>
                            <transition name="fadeLeft">
                                <span class='custom-alert' v-show="errors.has('Category')">{{ errors.first('Category') }}</span>
                               </transition>  
                      </div>
                      <div class="clearfix"> </div>
 <textarea name="Description" v-model='Description' v-validate='"required|max:4999"' required="">Description...</textarea>
 <transition name="fadeLeft">
    <span class='custom-alert' v-show="errors.has('Description')">{{ errors.first('Description') }}</span>
   </transition>
  </br>              
 <input type="submit" @click.prevent='post()'  v-if='submitBtn' value="Submit">
 <input type="submit" @click.prevent='update()' v-if='updateBtn' value="Update">  
 <input type="submit" @click.prevent='reverse()' v-if='reverseBtn' value="Reverse">  
                    </form>
                  </div>


                  <div class="col-md-6 contact-left">
                    <h6>Manage blog posts here</h6>
              <!--loading temp-->
              <transition name='anime' enter-active-class='animated fadeIn' :duration='200' leave-active-class='animated fadeOut'>
                  <div v-if='data_load'>
                    <template>
                        <v-progress-linear indeterminate></v-progress-linear>
                        Loading Data...
                      </template>
                    </div>
              </transition>
                    <!--loading temp-->

                    <transition name='anime' enter-active-class='animated fadeIn'  leave-active-class='animated fadeOut'>
                  <div class='table-responsive' v-if='data'>
                        <table class="table table-striped table-advance table-hover">
                            <tbody>
                               <tr>
                                  <th><v-icon>camera_alt</v-icon>Image</th>
                                  <th><v-icon>subject</v-icon> Title</th>
                                  <th><v-icon>subtitles</v-icon> Category</th>
                                  <th><v-icon>gavel</v-icon> Action</th>
                               </tr>
                               <tr v-for='con in content' v-bind:key='con.id'>
           <td><router-link :to="'/single/'+con.title.replace(/[.,/*%' '?!#{}$%+=`:;()@]/g,'-')+'/'+con.id">
          <v-img :src="'http://localhost:8000/storage/blog/'+con.image" class="img-thumbnail img-responsive size" alt=""
          :lazy-src="`http://localhost:8000/images/black-spinner.gif`"></v-img>
        </router-link></td>
           <td>{{con.title.substr(0,10)}}</td>
           <td>{{con.category}}</td>
                                <td>
                                   <div class="btn-group">
                <a class="btn btn-primary" href="#" @click.prevent='edit(con)'><i class="fa fa-pencil"></i></a>
                <a class="btn btn-danger" href="#" @click.prevent='removeProj(con.id)'><i class="fa fa-trash"></i></a>
                                   </div>
                                   </td>
                               </tr>
                                                          
                            </tbody>
                         </table>
<div class='text-center'>
<div class="pagination ">
<button class='btn btn-info' @click.prevent="fetch(pagination.prev_page_url)" :disabled="!pagination.prev_page_url" :loading='loading'>
Prev
</button>
                
<span>Page {{pagination.current_page}} of {{pagination.last_page}}</span>
                
<button class='btn btn-info' @click="fetch(pagination.next_page_url)" :disabled="!pagination.next_page_url" :loading='loading'>
 Next
</button>
</div>  
</div>

                       
                        
                    </div>
                    </transition>

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
        
        </template>
        

        
        <script>

            import axios from 'axios'

            export default {
              head(){
    return {
      title: "Henry's Onyemaobi",
      meta:[
        
          { hid: 'description7', name: 'description', content: "Henry Onyemaobi's, a web developer's portfolio website" },
          { name: 'keywords', content: 'website, web design, web application, web, web development, wordpress, php, html, web instructor, developer, porfolio, henry onyemaobi,website instructor, website teacher, pwa, spa, progressive web app, single page app,portfolio,web projects' },
        
      ]
    }
  },
                data(){
                  return{
                    Title: '',
                    Category: '',
                    load: false,
                    ImageFile: '',
                    Description: '',
                    valueDeterminate: 0,
                    blogct: 0,
                    projectct: 0,
                    conct:0,
                   subct:0,
                   //table data
                    content: [],
                    title: 'Create blogs here',
                    updateBtn: false,
                    submitBtn: true,
                    reverseBtn: false,
                    projId:'',
                    pagination:[],
                    loading: false,
                    data_load: true,
                    data: false,
                    stat_load:{'blog':true,'proj':true,'sub':true,'con':true},
                    valerror:[]
                  }
                },
    
    methods: {
    
        ImageSelect(event){
          this.ImageFile = event.target.files[0];
        },
    
        //post project
      post(){
        
          //validate
      this.$validator.validateAll().then(() => {
           
      if (!this.errors.any()) {
             //if no error
             this.load = true;
            // instantiant formdata object
       const formdata  = new FormData();
    //append form data to formdata
    formdata.append('ImageFile',  this.ImageFile);
    formdata.append('Title', this.Title);
    formdata.append('Category', this.Category);
    formdata.append('Description', this.Description);
    
    //send to database with axios
    axios.post('http://localhost:8000/api/save-blog',formdata).then(res=>{
  if(res.data == 1){
    
      alert("Blog Posted!");
      //clear in 3 secs
			setTimeout(func=>{
			
			},3000)
      this.load = false;
      this.valueDeterminate = 0;
   //clear form and errorbag
  this.Title ='';
  this.Description ='';
  this.Category ='';
	setTimeout(func=>{
		this.errors.clear()
	},1) 
	//clear form and errorbag
    
    //reload count
    this.blogcount();
    this.fetch();
  }else{
    alert("An Error Occured, Please contact Admin");
  }
  })
  .catch(error =>{
                  if(error.response.status == 422){
                    this.valerror = error.response.data.errors;
                    if(this.valerror){
                      alert("Please verify your information are correct...");
                    }
                  }
            this.$nuxt.$loading.finish()        
              })
    //here because if i leave it in the promise function, it will run till resolved
document.body.scrollTop = 0;
document.documentElement.scrollTop = 0;

     }else{
       //error occured
    alert('Validation errors detected...');    
    //clear in 3 secs
			setTimeout(func=>{
			
			},3000)
     }
    
    }); //validator
                     
                    
     },//post end

        blogcount(){
        axios.get('http://localhost:8000/blog-count')
        .then(res=>{
          this.blogct =res.data;
        })
        .catch(error =>{
       //  alert("Blog count failed...");
         this.stat_load.blog = true;
              })
        },

        projectcount(){
          axios.get('http://localhost:8000/proj-count')
        .then(res=>{
         this.projectct =res.data;
        })
        .catch(error =>{
        // alert("Project count failed...");
         this.stat_load.proj = true;
              })
        },
    
        subcount(){
          axios.get('http://localhost:8000/sub-count')
        .then(res=>{
         this.subct =res.data;
        })
        .catch(error =>{
        // alert("Subscription count failed...");
         this.stat_load.sub = true;
              })
        },

        contactcount(){
          axios.get('http://localhost:8000/contact-count')
        .then(res=>{
         this.conct =res.data;
        })
        .catch(error =>{
         alert("Stat data failed...Please reload page");
         this.stat_load.con = true;
              })
        },

 //fetch blogs
 fetch(page_url){
   if(page_url){
      // Start the route progress bar.
      this.$nuxt.$loading.start()
   }
          var   page_url = page_url || 'http://localhost:8000/blog-content';

          fetch(page_url)
          .then(res => res.json())
          .then(res=>{
            this.content = res.data;
            this.makePagination(res.meta, res.links);
            //turn off in here else...JS runs it before resolving promise
             // Start the route progress bar.
             this.$nuxt.$loading.finish()
          })
          .catch(error =>{
         alert("Blog data failed...Please reload page");
            this.$nuxt.$loading.finish()        
              })
        },

         makePagination(meta, links){
    var pagination = {
                    current_page: meta.current_page,
                    last_page: meta.last_page,
                    next_page_url: links.next,
                    prev_page_url: links.prev
                     }
    this.pagination = pagination;
    },

 edit(con){
          //prepare edit form
          document.body.scrollTop = 0;
		  	  document.documentElement.scrollTop = 0;
          this.updateBtn = true;
          this.submitBtn = false;
          this.reverseBtn = true;
          this.title = 'Update blog here';
          this.Title = con.title;
          this.Description = con.description;
          this.projId = con.id;
        },

        reverse(){
          this.updateBtn = false;
          this.submitBtn = true;
          this.title = 'Create blog here';
          this.Title = 'Enter a title..';
          this.Description = 'Enter a description..';
          this.reverseBtn = false;
        },

        update(){
          
      //validate
  this.$validator.validateAll().then(() => {
       
  if (!this.errors.any()) {
      this.load = true;
      //if no error
        // instantiant formdata object
   const formdata  = new FormData();
//append form data to formdata
formdata.append('ImageFile',  this.ImageFile);
formdata.append('Title', this.Title);
formdata.append('Category', this.Category);
formdata.append('Description', this.Description);
formdata.append('id', this.projId);

//send to database with axios
axios.post('http://localhost:8000/api/update-blog',formdata).then(res=>{
            if(res.data == 1){
              
                alert("Blog Updated!");
                //clear in 3 secs
			setTimeout(func=>{
			
			},3000)
              this.load = false;
              this.valueDeterminate = 0;
           
          //reloads
          this.fetch();
        }else{
          alert("An Error Occured, Please contact Admin");
        }
       })
       .catch(error =>{
                  if(error.response.status == 422){
                    this.valerror = error.response.data.errors;
                    if(this.valerror){
                      this.load = false;
                     this.valueDeterminate = 0;
                      alert("Please verify your information are correct...");
                    }
                  }
            this.$nuxt.$loading.finish()        
              })
//here because if i leave it in the promise function, it will run till resolved
document.body.scrollTop = 0;
document.documentElement.scrollTop = 0;
 }else{
   //error occured
alert('Validation errors detected...');    
//clear in 3 secs
setTimeout(func=>{
			
			},3000)
 }

}); //validator
   
  },


  

removeProj(id){
    this.projId = id;
  //toggle loading
  this.loading = true;
  var input =  {'id':this.projId};
  axios.post('http://localhost:8000/api/destroy-blog',input)
  .then(res=>{
    if(res.data == 1){
        alert("Blog post deleted!");
       
          //reloads
          
          this.fetch();
          this.blogcount();
          //toggle loading
          this.loading = false;
        }else{
          alert("An Error Occured, Please contact Admin");
        }
  })
  .catch(error =>{
    this.loading = false;
    
         alert("Delete failed...");
            this.$nuxt.$loading.finish()           
              })
},

clearModal(){
this.$modal.hide('delete');
}

    },//meth end
    

    mounted() {
        
//call methods on load
       this.blogcount();
       this.projectcount();
       this.subcount();
       this.contactcount();
      this.fetch();
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

    //watch stat counts
    blogct(a,b){
      if(a){
        //show blog count
        this.stat_load.blog = false;
      }
    },
    projectct(a,b){
      if(a){
       //show project count
       this.stat_load.proj = false;
      }
    },
    conct(a,b){
      if(a){
       //show con count
       this.stat_load.con = false;
      }
    },
    subct(a,b){
      if(a){
       //show sub count
       this.stat_load.sub = false;
      }
    },

//watch end
},
        
    }
        </script>



