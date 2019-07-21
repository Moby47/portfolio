<template>
		<v-app id="inspire">

		
	
	<!-- **************************body********************************** -->
		    <v-content>
			<v-container fluid>
	
			<!-- ************************** content********************************** -->
            <div class="body-back">
                    <div class="masthead pdng-stn1">
                        
                        <div class="phone-box wrap push" id="home">
                        
                            <!--/blog-->
                            <div class="services-section">
                                <div class="wrap_view_agileits">
                                    <div class="inner_section_wthree">
                                        <!--loading temp-->
<div v-if='load'>
        <template>
            <v-progress-circular v-model="valueDeterminate"></v-progress-circular>
          </template>
        </div>
        <!--loading temp-->
                                        <div class="col-md-7 contact_grid_right">
                                            <h6>Kindly Leave a Review.</h6>
                                            <form action="#" method="post">
                                                <div class="col-md-6 col-sm-6 contact_left_grid">
                                   <input type="text" v-model='Name' v-validate='"required|max:49"' name="Name" placeholder="First Name Only" required="">
                                   <transition name="fadeLeft"> 
                                        <span  class='custom-alert' v-show="errors.has('Name')">{{ errors.first('Name') }}</span>
                                       </transition>         
                                </div>
                                                <div class="clearfix"> </div>
          <textarea v-model='Message' v-validate='"required|max:254"' name="Message"  required="" placeholder="Message..."></textarea>
                                   <transition name="fadeLeft">
                                        <span class='custom-alert' v-show="errors.has('Message')">{{ errors.first('Message') }}</span>
                                       </transition> 
                                       <br>
                                   <input type="submit" @click.prevent='go' value="Submit">
                                            </form>
                                        </div>
                                        <div class="col-md-5 contact-left">
                                            
                                            
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
        <!-- ************************** content********************************** -->
        
			</v-container>
		  </v-content>
	
	
		</v-app>
      </template>
     
	  <script>

          import axios from 'axios'
		export default {
            	 //meta
               head(){
    return {
      title: "Henry's Onyemaobi portfolio website",
      meta:[
        
          { hid: 'description', name: 'description', content: "PLease leave a kind review on Henry Onyemaobi's Portfolio website" },
          { name: 'keywords', content: 'website, web design, web application, web, web development, wordpress, php, html, web instructor, developer, porfolio, henry onyemaobi,website instructor, website teacher, pwa, spa, progressive web app, single page app,portfolio,web projects' },
        
      ]
    }
  },
        //meta
		  data: () => ({
			drawer: null,
            Name:'',
            Message:'',
            load: false,
            valueDeterminate: 0,
            valerror:[]
          }),

          mounted(){
            
            document.body.scrollTop = 0;
			document.documentElement.scrollTop = 0;

            var input = {'pass':this.$route.params.pass}
              axios.post('http://localhost:8000/api/link-validate', input)
              .then(res=>{
                  if(res.data == 1){
                    alert('welcome! Please drop a kind review')
                     //clear toasted in 3 secs
			setTimeout(func=>{
			
             },5000)
            //clear toasted in 3 secs
                  }else{
                      alert('You are not authorized to use this page');
                      //redirect
                      this.$router.push({name: "index"});
                  }
                  
              })
             

          },

          methods: {

            go(){
        
                  //validate
     this.$validator.validateAll().then(() => {
       
       if (!this.errors.any()) {
             // Start the route progress bar.
             this.$nuxt.$loading.start()
        var input = {Name: this.Name, Message: this.Message};
                axios.post('http://localhost:8000/api/leave-review',input)
            .then(res=>{
        if(res.data == 1){
            alert("Review Successful!");
            //clear in 3 secs
			setTimeout(func=>{
			
            },3000)
             //clear form and errorbag
            this.Name ='';
            this.Message ='';
                setTimeout(func=>{
                    this.errors.clear()
                },1) 
	//clear form and errorbag
        }else{
            alert("An Error Occured, Please contact Admin");
        }
        this.$nuxt.$loading.finish()
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
      }else{
        //error occured
     alert('Validation errors detected...');    
     //clear in 3 secs
			setTimeout(func=>{
			
			},3000)
      }
     
     })
       },

          },

		  props: {
			source: String
		  },
		
		}
	  </script>


