<template>

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
						<h3 class="head">Contact Me</h3>
						<div class="inner_section_wthree">
							<div class="col-md-7 contact_grid_right">
								<h6>Please fill this form.</h6>
								<form action="#" method="post">
									<div class="col-md-6 col-sm-6 contact_left_grid">
										<input type="text" v-model='Name' v-validate='"required|max:49"' name="Name" placeholder="Name" required="">
										<transition  name="fadeLeft">
												<span class='custom-alert' v-show="errors.has('Name')">{{ errors.first('Name') }}</span>
											   </transition> 
										<input type="email" v-model='Email' v-validate='"required|email"' name="Email" placeholder="Email" required="">
										<transition  name="fadeLeft">
												<span class='custom-alert' v-show="errors.has('Email')">{{ errors.first('Email') }}</span>
											   </transition> 
									</div>
									<div class="col-md-6 col-sm-6 contact_left_grid">
										<input type="text" v-model='Telephone' v-validate='"required|digits:11"' name="Telephone" placeholder="Telephone" required="">
										<transition name="fadeLeft">
												<span class='custom-alert' v-show="errors.has('Telephone')">{{ errors.first('Telephone') }}</span>
											   </transition> 
											
										<input type="text" v-model='Subject' v-validate='"required|max:50"' name="Subject" placeholder="Subject" required="" class='push-up'>
										<transition name="fadeLeft">
												<span class='custom-alert' v-show="errors.has('Subject')">{{ errors.first('Subject') }}</span>
											   </transition> 
									</div>
									<div class="clearfix"> </div>
					<textarea name="Message" v-model='Message' v-validate='"required|max:254"' onfocus="this.value = '';" onblur="if (this.value == '') {this.value = 'Message...';}" required="">Message...</textarea>
					<transition name="fadeLeft">
							<span class='custom-alert' v-show="errors.has('Message')">{{ errors.first('Message') }}</span>
						   </transition> 	
						   <br>		
		<v-btn class='custombtn primary' :loading='loading' type="submit" @click.prevent='contact'>Submit</v-btn> 
								</form>
							</div>
							<div class="col-md-5 contact-left">
								<h6>Quick Contact</h6>
								<p>
								Contact me for your customized web applications and  websites.
								</p>
								<div class="mail-us">
									<div class="col-md-2 col-sm-2 col-xs-2 contact-icon">
										<span class="fa fa-envelope" aria-hidden="true"></span>
									</div>
									<div class="col-md-10 col-sm-10 col-xs-10 contact-text">
										<h4>Email</h4>
										<p><a href="mailto:support@henrymoby.tech">Click here</a></p>
									</div>
									<div class="clearfix"></div>
								</div>
								<div class="call">
									<div class="col-md-2 col-sm-2 col-xs-2 contact-icon">
										<span class="fa fa-phone" aria-hidden="true"></span>
									</div>
									<div class="col-md-10 col-sm-10 col-xs-10 contact-text">
										<h4>Call</h4>
										<p><a href="tel:+2348035562231">Click here</a></p>
									</div>
									<div class="clearfix"></div>
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

</template>

<style scoped>
		.custombtn{
		  background-color: #123c69 !important;
		  color:white;
		}
	  </style>

<script>
    import axios from 'axios'
    
    export default {
		head(){
    return {
      title: "Contact Henry",
      meta:[
        
          { hid: 'description', name: 'description', content: 'Meet Henry! a goal driven web developer dedicated to creating, designing, developing professional web applications and websites' },
          { name: 'keywords', content: 'website, web design, web application, web, web development, wordpress, php, html, web instructor, developer, porfolio, henry onyemaobi,website instructor, website teacher, pwa, spa, progressive web app, single page app,portfolio,web projects' },
        
      ]
    }
  },
        data(){
			return{
				Name: '',
				Email: '',
				Telephone:'',
				Subject: '',
				Message: '',
				loading: false,
				valerror:[]
			}
		},

		methods:{
			contact(){
	 
          //validate
      this.$validator.validateAll().then(() => {
           
      if (!this.errors.any()) {
			 //if no error
			 //toggle loading
			 this.loading = true;
			 this.$nuxt.$loading.start()
            // instantiant formdata object
       const formdata  = new FormData();
    //append form data to formdata
    formdata.append('Name',  this.Name);
    formdata.append('Email', this.Email);
    formdata.append('Subject', this.Subject);
	formdata.append('Telephone', this.Telephone);
	formdata.append('Message', this.Message);
    
    //send to database with axios
	console.log('before')
	console.log(formdata)
    axios.post('http://localhost:8000/api/contact',formdata)
	.then(res=>{
	console.log('after')
  if(res.data == 1){
	this.$nuxt.$loading.finish()
	alert("Thank you! You will be contacted shortly.");
  }else{
	this.$nuxt.$loading.finish()
    alert("An Error Occured, Please call me");
  }
     //toggle loading
	 this.loading = false;
  })
  .catch(err=>{
	  //toggle loading
	  console.log(err)
	  this.$nuxt.$loading.finish()
	 this.loading = false;
  })
	//clear form and errorbag
	this.Name = '';
	this.Email ='';
	this.Telephone= '';
	this.Subject= '';
	this.Message= '';
	setTimeout(func=>{
		this.errors.clear()
	},1) 
	//clear form and errorbag
 
     }else{
       //error occured
     }
    
	}); //validator
	
			}
		},

		mounted(){
			
		}
		

    }
</script>