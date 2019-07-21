<template>
    <div>


        <!--floating left
      <v-btn 
      fab 
      dark
      color="info"
      small
      relative
      bottom
      left
      fixed
        >
      <v-icon dark>android</v-icon>
      </v-btn>
      floating left-->
  
       <!--floating right-->
       <v-btn 
       fab 
       dark
       color="#ac3b61"
       small
       relative
       bottom
       right
       fixed
         >
       <v-icon dark @click='up()'>arrow_upward</v-icon>
       </v-btn>

             <!--floating right-->
            </div>
        </template>   



        <script>
        
        export default{
            methods: {
                          up(){
                            document.body.scrollTop = 0;
													document.documentElement.scrollTop = 0;
													},
												/*	
												scroll(event){
														console.log(event);
													}
													*/
											},
        }
        </script>