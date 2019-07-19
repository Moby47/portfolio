<template>
 
        <!-- main -->
        <div class="body-back">
          <div class="masthead pdng-stn1">
  
  
          <!--menu-ui -->

                  <!-- banner -->
                  <div class="banner_info_agile_w3ls">
                      <div class='dark-over '>

                      <div class="banner_info_agile_w3ls_inner bounceIn">
                          <img src="~assets/images/Henry onyemaobi web developer.jpg" 
                          alt="Henry onyemaobi web developer portfolio"
                           class="img-responsive " title='Henry onyemaobi web developer'>
                          <h2>I'm Henry</h2>
                          <span>Web Developer</span>
                          <ul class="top-links_w3layouts padd ">
                               <li><a href="https://www.linkedin.com/in/henry-onyemaobi" target='_blank'><i class="fa fa-linkedin"></i></a></li>
                              <li><a href="mailto:support@henrymoby.tech"><i class="fa fa-google-plus"></i></a></li>
                              <li><a href="https://github.com/Moby47" target='_blank'><i class="fa fa-github"></i></a></li>
                              <li><a href="https://api.whatsapp.com/send?phone=+2348035562231"><i class="fa fa-whatsapp"></i></a></li>
                              <li><a href="https://www.facebook.com/mobyf" target='_blank'><i class="fa fa-facebook"></i></a></li>
                          </ul>
                      </div>

                  </div>
                  </div>
                  <!--// banner -->
                  <!-- about -->
                  <div class="about">
                      <div class="wrap_view_agileits">
                          <h3 class="head">About Me</h3>
                          <p class="head_para">A goal driven web developer</p>
                          <div class="inner_section_wthree">
                              <div class="col-md-7 about-left">
                                  <div class="about-left-info">
                                          <h4>Name</h4>
                                          <p>Henry Nnamdi Onyemaobi</p>
                                  </div>
                                  <div class="about-left-info">
                                          <h4>Sex</h4>
                                          <p>Male</p>
                                      </div>
                                  <div class="about-left-info">
                                          <h4>Job Title</h4>
                                          <p>Web Developer</p>
                                  </div>
                                  <div class="about-left-info">
                                      <h4>Address</h4>
                                      <p>Lekki Gardens. Lagos</p>
                                  </div>
                                  <div class="about-left-info">
                                      <h4>Email Address</h4>
                                      <p><a href="mailto:support@henrymoby.tech">support@henrymoby.tech</a></p>
                                  </div>
                              </div>

                              <div class="col-md-5 ab-right wow bounceIn">
                                      <div class="about-right-img">
                                      <template>
                                              <v-hover>
                                                <v-card
                                                  slot-scope="{ hover }"
                                                  :class="`elevation-${hover ? 17 : 2}`"
                                                  class="mx-auto"
                                                >
                                                  <v-img
                                                    :aspect-ratio="16/22"
                                                    src="http://localhost:8000/images/Henry onyemaobi.jpg"
                                                    :lazy-src="`http://localhost:8000/images/black-spinner.gif`"
                                                    alt='Henry onyemaobi, website designer in lagos'
                                                  ></v-img>
                                                 
                                                </v-card>
                                              </v-hover>
                                            </template>
                                            </div>
                              </div>


                              <div class="clearfix"> </div>
                          </div>
                      </div>
                  </div>
                  <!-- //about-bottom -->
                  
                  <!--/education-->
                  <div class="education_sec">

                      <div class="col-md-6 ">
                              <template>
                                      <v-parallax
                                          class='pix-edit '
                                        height="325"
                                        alt='henry onyemaobi website developer in lagos'
                                        src="_nuxt/assets/images/edu.jpg"
                                        :lazy-src="`_nuxt/assets/images/black-spinner.gif`"
                                      ></v-parallax>
                                    </template>
                      </div>

                      <div class="education_sec">
                      <div class="col-md-6 education-main ">
                          <h3 class="head">My Education</h3>
                          <div class="education-grids wow zoomer">
                                  <div class="education two">
                                          <div class="education-year ">
                                              <h5 class='text-white'>2018-2019</h5>
                                              <h6 class='text-white'>PGD</h6>
                                          </div>
                                          <div class="education-info">
                                              <h4>Babcock University</h4>
                                              <p>Post Graduate Diploma in Computer Science.</p>
          
                                          </div>
                                          <div class="clearfix"></div>
                                      </div>
                              <div class="education">
                                  <div class="education-year ">
                                      <h5 class='text-white'>2011-2015</h5>
                                      <h6 class='text-white'>BSc</h6>
                                  </div>
                                  <div class="education-info">
                                      <h4>Benue State University</h4>
                                      <p>Bachelor of Science in Computer Science. </p>
  
                                  </div>
                                  <div class="clearfix"></div>
                              </div>
                          
                              
                          </div>
                      </div>
                      </div>
  
                      <div class="clearfix"> </div>
                  </div>
  
                  <!--//education-->
                  <!--/experience-->
                  <div class="education_sec">
                      <div class="col-md-6 education-main ">
                          <h3 class="head">My Experience</h3>
                          <div class="education-grids wow zoomer">
                              <div class="education">
                                  <div class="education-year ">
                                      <h5 class='text-white'>2017-2018</h5>
                                      <h6 class='text-white'>HiiT Plc Lagos</h6>
                                  </div>
                                  <div class="education-info">
                                      <h4>Web Development</h4>
                                      <p>Tutored aspiring Web developers Using several front and backend
                                          web technologies.</p>
                                  </div>
                                  <div class="clearfix"></div>
                              </div>
                              <div class="education two">
                                  <div class="education-year ">
                                      <h5 class='text-white'>2014-2015</h5>
                                      <h6 class='text-white'>HiiT Plc Abuja</h6>
                                  </div>
                                  <div class="education-info">
                                      <h4>Microsoft Office Instructor</h4>
                                      <p>Tutored students on Microsoft suite package and computer 
                                              fundamentals.</p>
                                  </div>
                                  <div class="clearfix"></div>
                              </div>
                          
                          </div>
                      </div>
                      <div class="col-md-6">
                              <template>
                                      <v-parallax
                                      class='pix-edit'
                                        height="370"
                                        alt='henry onyemaobi, a web developer in lagos'
                                        src="_nuxt/assets/images/exp.jpg"
                                        :lazy-src="`_nuxt/assets/images/black-spinner.gif`"
                                      ></v-parallax>
                                    </template>
                      </div>
  
                      <div class="clearfix"> </div>
                  </div>
                  <!--//experience-->
                 
                 
                  
                  <!--/skill-->
                  <div class="education_sec">
                      <div class="col-md-6 education-main ">
                          <div class="education-grids">
                              <div class="education">
                                  <!--1 left-->
                                  <div class="skillname">
                                      <img 
                                      src='~assets/images/skills/language-html5.svg'
                                      alt='web / website developer in lagos'
                                       
                                      >
                                  </div>
                                  <div class="education-info level">
                                          <template>
                                                  <div>
                                                    <v-progress-linear
                                                      color="grey"
                                                      height="20"
                                                      value="95.5"
                                                    ><span class='percent'>95.5%</span></v-progress-linear> 
                                                  </div>
                                                </template>
                                  </div>
                                  <div class="clearfix"></div>
                                  <!--1-->
                                   <!--1 left-->
                                   <div class="skillname">
                                          <img 
                                          src="~assets/images/skills/language-css3.svg"
                                          alt='web / website developer in lagos'
                                           
                                          >
                                      
                                      </div>
                                      <div class="education-info level">
                                              <template>
                                                      <div>
                                                        <v-progress-linear
                                                          color="grey"
                                                          height="20"
                                                          value="80"
                                                        ><span class='percent'>80%</span></v-progress-linear> 
                                                      </div>
                                                    </template>
                                      </div>
                                      <div class="clearfix"></div>
                                      <!--1-->
                                         <!--1 left-->
                                  <div class="skillname">
                                          <img 
                                          src='~assets/images/skills/js.svg'
                                          alt='web / website developer in lagos'
                                           
                                          >
                                      
                                      </div>
                                      <div class="education-info level">
                                              <template>
                                                      <div>
                                                        <v-progress-linear
                                                          color="grey"
                                                          height="20"
                                                          value="70.5"
                                                        ><span class='percent'>70.5%</span></v-progress-linear> 
                                                      </div>
                                                    </template>
                                      </div>
                                      <div class="clearfix"></div>
                                      <!--1-->
                                         <!--1 left-->
                                  <div class="skillname">
                                          <img 
                                          src='~assets/images/skills/bootstrap.svg'
                                          alt='web / website developer in lagos'
                                           
                                          >
                                      
                                      </div>
                                      <div class="education-info level">
                                              <template>
                                                      <div>
                                                        <v-progress-linear
                                                          color="grey"
                                                          height="20"
                                                          value="85"
                                                        ><span class='percent'>85%</span></v-progress-linear> 
                                                      </div>
                                                    </template>
                                      </div>
                                      <div class="clearfix"></div>
                                      <!--1-->
                                         <!--1 left-->
                                  <div class="skillname">
                                          <img 
                                          src='~assets/images/skills/jquery.svg'
                                          alt='web / website developer in lagos'
                                           
                                          >
                                      
                                      </div>
                                      <div class="education-info level">
                                              <template>
                                                      <div>
                                                        <v-progress-linear
                                                          color="grey"
                                                          height="20"
                                                          value="75"
                                                        ><span class='percent'>75%</span></v-progress-linear> 
                                                      </div>
                                                    </template>
                                      </div>
                                      <div class="clearfix"></div>
                                      <!--1-->
                                       <!--1 left-->
                                  <div class="skillname">
                                          <img 
                                          src='~assets/images/skills/vuejs.svg'
                                          alt='web / website developer in lagos'
                                           
                                          >
                                      
                                      </div>
                                      <div class="education-info level">
                                              <template>
                                                      <div>
                                                        <v-progress-linear
                                                          color="grey"
                                                          height="20"
                                                          value="75.9"
                                                        ><span class='percent'>75.9%</span></v-progress-linear> 
                                                      </div>
                                                    </template>
                                      </div>
                                      <div class="clearfix"></div>
                                      <!--1-->
                              </div>
                          </div>
                      </div>










                      <div class="col-md-6 education-main ">
                              <div class="education-grids">
                                  <div class="education">
                                      <!--1 right-->
                                      <div class="skillname">
                                              <img 
                                              src='~assets/images/skills/language-php.svg'
                                              alt='web / website developer in lagos'
                                               
                                              >
                                          
                                          </div>
                                          <div class="education-info level">
                                                  <template>
                                                          <div>
                                                            <v-progress-linear
                                                              color="grey"
                                                              height="20"
                                                              value="80"
                                                            ><span class='percent'>80%</span></v-progress-linear> 
                                                          </div>
                                                        </template>
                                          </div>
                                          <div class="clearfix"></div>
                                      <!--1-->
                                      <!--1 right-->
                                      <div class="skillname">
                                              <img 
                                              src='~assets/images/skills/laravel.svg'
                                              alt='web / website developer in lagos'
                                               
                                              >
                                          
                                          </div>
                                          <div class="education-info level">
                                                  <template>
                                                          <div>
                                                            <v-progress-linear
                                                              color="grey"
                                                              height="20"
                                                              value="87"
                                                            ><span class='percent'>87%</span></v-progress-linear> 
                                                          </div>
                                                        </template>
                                          </div>
                                          <div class="clearfix"></div>
                                      <!--1-->
                                      <!--1 right-->
                                      <div class="skillname">
                                              <img 
                                              src='~assets/images/skills/database.svg'
                                              alt='web / website developer in lagos'
                                               
                                              >
                                          
                                          </div>
                                          <div class="education-info level">
                                                  <template>
                                                          <div>
                                                            <v-progress-linear
                                                              color="grey"
                                                              height="20"
                                                              value="75"
                                                            ><span class='percent'>75%</span></v-progress-linear> 
                                                          </div>
                                                        </template>
                                          </div>
                                          <div class="clearfix"></div>
                                      <!--1-->
                                      <!--1 right-->
                                      <div class="skillname">
                                              <img 
                                              src='~assets/images/skills/wordpress.svg'
                                              alt='web / website developer in lagos'
                                               
                                              >
                                          
                                          </div>
                                          <div class="education-info level">
                                                  <template>
                                                          <div>
                                                            <v-progress-linear
                                                              color="grey"
                                                              height="20"
                                                              value="70"
                                                            ><span class='percent'>70%</span></v-progress-linear> 
                                                          </div>
                                                        </template>
                                          </div>
                                          <div class="clearfix"></div>
                                      <!--1-->
                                      <!--1 right-->
                                      <div class="skillname">
                                              <img 
                                              src='~assets/images/skills/github.svg'
                                              alt='web / website developer in lagos'
                                               
                                              >
                                          
                                          </div>
                                          <div class="education-info level">
                                                  <template>
                                                          <div>
                                                            <v-progress-linear
                                                              color="grey"
                                                              height="20"
                                                              value="60"
                                                            ><span class='percent'>60%</span></v-progress-linear> 
                                                          </div>
                                                        </template>
                                          </div>
                                          <div class="clearfix"></div>
                                      <!--1-->
                                       
                                          
                                  </div>
                              </div>
                          </div>
                  </div>
                  <!--//skill-->

                  <!--//footer-->
                  <!--//footer-->
  
              </div>
          </div>
      </div>
      <!-- main -->
</template>

<style>
  .skillname{
        float: left;
        width: 60px !important;
        height: 30px !important;
        padding-left: 14px;
        padding: .5em 1em;
    }
    .level {
    width: 89% !important;
    }
    .percent{
        margin-left:50%;
        color:white;
    }
</style>

<script>
//import Thefooter from '~/components/Thefooter.vue'

export default {
  components: {
   // Thefooter,
  },
  head(){
    return {
      title: "Henry's Web Development Portfolio Website",
      meta:[
        
          { hid: 'description', name: 'description', content: 'Meet Henry! a goal driven web developer dedicated to creating, designing, developing professional web applications and websites' },
          { name: 'keywords', content: 'website, web design, web application, web, web development, wordpress, php, html, web instructor, developer, porfolio, henry onyemaobi,website instructor, website teacher' },
        
      ]
    }
  },
}
</script>
