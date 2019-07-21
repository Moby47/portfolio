<template>
  <v-app >
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>

        <v-list-tile
        v-if='isauth() === true'
          to="/manage-blog"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon>speaker_notes</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            Manage blog
          </v-list-tile-content>
        </v-list-tile>

        <v-list-tile
        to="/manage-project"
        router
        exact
        v-if='isauth() === true'
      >
        <v-list-tile-action>
          <v-icon>build</v-icon>
        </v-list-tile-action>
        <v-list-tile-content>
          Manage project
        </v-list-tile-content>
      </v-list-tile>

      <v-list-tile
      @click.prevent='exportmaillist'
      to=""
      router
      exact
      v-if='isauth() === true'
    >
      <v-list-tile-action>
        <v-icon>mail</v-icon>
      </v-list-tile-action>
      <v-list-tile-content>
        Mail list
      </v-list-tile-content>
    </v-list-tile>

    <v-list-tile
    to="/generate"
    router
    exact
    v-if='isauth() === true'
  >
    <v-list-tile-action>
      <v-icon>link</v-icon>
    </v-list-tile-action>
    <v-list-tile-content>
      Generate review link
    </v-list-tile-content>
  </v-list-tile>


  <v-list-tile
  @click.prevent='logout()'
  to=""
  router
  exact
  v-if='isauth() === true'
>
  <v-list-tile-action>
    <v-icon>power_off</v-icon>
  </v-list-tile-action>
  <v-list-tile-content>
    Logout
  </v-list-tile-content>
</v-list-tile>


  <v-list-tile
  to="/review/4747"
  router
  exact
  v-if='isauth() === true'
>
  <v-list-tile-action>
    <v-icon>link</v-icon>
  </v-list-tile-action>
  <v-list-tile-content>
    Review
  </v-list-tile-content>
</v-list-tile>


<v-list-tile
  to=""
  router
  exact
  v-if='isauth() != true'
  @click.prevent='dialog = true'
>
  <v-list-tile-action>
    <v-icon>account_circle</v-icon>
  </v-list-tile-action>
  <v-list-tile-content>
    Admin
  </v-list-tile-content>
</v-list-tile>

      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-side-icon @click="drawer = !drawer" />
     
    </v-toolbar>
    
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
   
    <float/> 

    <v-footer
    dark
    height="auto"
  >
    <v-card
      flat
      tile
      class=" text-xs-center"
      color='#123c69'
    >
     <br>
     <br>
      <v-card-text class="white--text pt-0 ">
        It is essential to stay relevant in this world, the Internet is another world we live in today, 
        go LIVE! with an outstanding web platform today!  <router-link to='/contact' class=' badge'> Contact Me</router-link>
        . I am professionally inclined to design your needed website in view of achieving the desired goals.
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text ">
        &copy;2019 — <strong>MobyTech</strong>
      </v-card-text>
    </v-card>
  </v-footer>




  <template>
    <v-layout row justify-center>
      <v-dialog v-model="dialog"  max-width="600px">
        <template v-slot:activator="{ on }">
         
        </template>
        <v-card>
          <v-card-title>
            <span class="headline">Admin Area</span>
          </v-card-title>
          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>

                <v-flex xs12>
                  <v-text-field label="Email*" required
                  v-model='Email' v-validate='"required|email"' name="Email"></v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-text-field v-model='Password' v-validate='"required"' name="Password"
                   label="Password*" type="password" required></v-text-field>
                </v-flex>

              </v-layout>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click.prevent='login()' :loading='loading'>Login</v-btn>
            <v-btn color="blue darken-1" flat @click="dialog = false">Close</v-btn>
           
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-layout>
  </template>
  </v-app>
</template>

<script>
  
  import float from '~/components/float.vue'
  import axios from 'axios'

  //axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components:{
			float
		},
  head () {
    return {
    }
  },

  data() {
    return {
      dialog: false,
      mail:'',
            pass:'',
            loading:false,
            confirmedP: '',
            Email:'',
            Password:'',
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'home',
          title: 'MobyTech',
          to: '/'
        },
        {
          icon: 'work',
          title: 'Services',
          to: '/services'
        },
        {
          icon: 'build',
          title: 'Projects',
          to: '/projects'
        },
        {
          icon: 'speaker_notes',
          title: 'Blog',
          to: '/blog'
        },
        {
          icon: 'contact_support',
          title: 'Contact Me',
          to: '/contact'
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  },

  methods: {

login(){
this.loading = true;
this.$nuxt.$loading.start()

     var input = {'email':this.Email, 'password':this.Password};
     
     axios.post('http://localhost:8000/api/admin-login',input)
     .then(res => {
           var token = res.data.token;
          // console.log('token is  ' + token);
           if(token){
                 localStorage.setItem('token',token);
                 this.isauth();
                 alert('Login successful!');
                 this.dialog = false;
                 this.drawer = true;
           }else{
                 var token = null;   
                 alert('Login failed, please verify credentials...');
                 
           }

           this.loading = false;
           this.$nuxt.$loading.finish()
     })
     .catch(error =>{
       alert('Login failed...');
       this.loading = false;
           this.$nuxt.$loading.finish()
     })
    }, //login

exportmaillist(){
 axios({
   url: 'http://localhost:8000/api/downloadExcel',
   method: 'GET',
   responseType: 'blob', // important
 }).then((response) => {
   const url = window.URL.createObjectURL(new Blob([response.data]));
   const link = document.createElement('a');
   link.href = url;
   link.setAttribute('download', 'Maillist.csv'); //or any other extension
   document.body.appendChild(link);
   link.click();
 });
},

   isauth(){
     /*
    if(process.browser){
      if(localStorage.getItem('token')){
      
           return true;
     }else{
     
           return false;
     }
    }
     */
      },


       logout(){
        this.$nuxt.$loading.start();
      localStorage.removeItem('token');
      this.isauth();
      
      console.log('logged out');
       this.$router.push({name:'index'});
       this.drawer = false;
       this.$nuxt.$loading.finish();
       },

},
mounted(){
  this.isauth()
}

}
</script>
