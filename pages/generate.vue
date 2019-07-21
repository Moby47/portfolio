<template>
		<v-app id="inspire">
      
      <!-- **************************body********************************** -->
            <v-content>
          <v-container fluid>
      
          <!-- ************************** content********************************** -->
          <template>

                <div class="body-back">
                    <div class="masthead pdng-stn1">
                        
                        <div class="phone-box wrap push" id="home">
                        
                            <!--/blog-->
                            <div class="services-section">
                                <div class="wrap_view_agileits">
                                    <div class="inner_section_wthree">
        
        
                                        <div class="col-md-12 contact_grid_right text-center">
                                                <h6>Generate Review Link For Clients</h6>
                                            <form action="#" method="post">
                                              <p>{{link}}</p>
                                               <br>
                                                <div class="clearfix"> </div>
                         <v-btn type="submit" @click.prevent='generate'  :loading='loading' class='custombtn'>Generate</v-btn>
                                            </form>
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
      title: "Henry's Onyemaobi",
      meta:[
        
          { hid: 'description', name: 'description', content: "Henry Onyemaobi's, a web developer's portfolio website" },
          { name: 'keywords', content: 'website, web design, web application, web, web development, wordpress, php, html, web instructor, developer, porfolio, henry onyemaobi,website instructor, website teacher, pwa, spa, progressive web app, single page app,portfolio,web projects' },
        
      ]
    }
  },
        //meta
		  data: () => ({
            drawer: null,
            link:'',
            loading:false,
          }),
          
		  props: {
			source: String
          },

          methods: {
              up(){
                window.scrollTo(0, 1);
              },

              generate(){
                
                //toggle loading
                this.loading = true;
                  //goto server,generate link,save and send back
            axios.post('http://localhost:8000/api/get-review-link')
            .then(res =>{
                //final link
             this.link  = res.data;
             alert('link generated!');
              //clear toasted in 3 secs
			setTimeout(func=>{
			
             },3000)
            //clear toasted in 3 secs
             //toggle loading
             this.loading = false;
            })
                
              }
          },

          mounted(){
            
            document.body.scrollTop = 0;
			document.documentElement.scrollTop = 0;
          }
		}
	  </script>


