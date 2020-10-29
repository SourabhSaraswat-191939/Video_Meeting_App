<template>
<main>

  <v-carousel v-model="model" 
    height="90vh" 
    show-arrows-on-hover 
    hide-delimiter-background 
    
    >


    <v-fab-transition>
      <v-btn
        absolute
        fab
        small
        dark
        right
        @click="group_drawer = true"
      >
        <v-icon>mdi-account-group</v-icon>
      </v-btn>
    </v-fab-transition>
    



<!-- chat drawer -->
<v-navigation-drawer
      v-model="chat_drawer"
      absolute
      right
      temporary
      width="30%"
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
        <v-title>GROUP CHAT</v-title>
        <v-divider />
          <v-list-item>
            <v-text-field
            v-model="first"
            label="Hey !"
            solo
            rounded
            style="margin-right:20%;"
          ></v-text-field>
          </v-list-item>

            <v-list-item>
            <v-text-field
            v-model="first"
            label="Hi"
            solo
            rounded
            style="margin-right:20%;"

          ></v-text-field>
          </v-list-item>
          <v-list-item>
            <v-text-field
            v-model="first"
            label="Hi"
            solo
            rounded
            style="margin-left:20%;"
          ></v-text-field>
          </v-list-item>
          <v-list-item>
            <v-text-field
            v-model="first"
            label="Whats Up!"
            solo
            rounded
            style="margin-right:20%;"

          ></v-text-field>
          </v-list-item>
          <v-list-item>
            <v-text-field
            v-model="first"
            label="Good"
            solo
            rounded
            style="margin-right:20%;"

          ></v-text-field>
          </v-list-item>
          
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>







<!-- peoples in class drawer -->
<v-navigation-drawer
      v-model="group_drawer"
      absolute
      right
      temporary
      light
      width="30%"
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
        <v-title>CLASSROOM</v-title>
        <v-divider />
          



        <v-virtual-scroll
        :bench="benched"
        :items="items"
        height="700"
        item-height="64"
      >
        <template v-slot:default="{ item }">
          <v-list-item :key="item">
            <v-list-item-action>
              <v-btn
                fab
                small
                depressed
                color="primary"
              >
                {{ item }}
              </v-btn>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>
                User Database Record <strong>ID {{ item }}</strong>
              </v-list-item-title>
            </v-list-item-content>

            <v-list-item-action>
              <v-icon small>
                mdi-open-in-new
              </v-icon>
            </v-list-item-action>
          </v-list-item>

          <v-divider></v-divider>
        </template>
      </v-virtual-scroll>




          
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>














    <v-carousel-item
      v-for="(color, i) in colors"
      :key="color"
    >
      <v-sheet
        :color="color"
        height="100%"
        tile
      >
        <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
          <div class="display-3">
            Slide {{ i + 1 }}
          </div>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>


<v-bottom-navigation
    height="10vh"
    v-model="value"
    :background-color="color"
    dark
    shift
  >

    <v-btn style="position:absolute;left:0;height:10vh;width:5%" :color="mic? `blue`:``" @click="mic=!mic">
        <span v-if="mic">Mic</span>
        <span v-else>Mic OFF</span>
        <v-icon v-if="mic">mdi-microphone</v-icon>
        <v-icon v-else>mdi-microphone-off</v-icon>
    </v-btn>
    <v-btn style="position:absolute;left:5%;height:10vh" :color="video? `blue`:``" @click="video=!video">
        <span v-if="video">Video</span>
        <span v-else>Video OFF</span>
        <v-icon v-if="video">mdi-video</v-icon>
        <v-icon v-else>mdi-video-off</v-icon>
    </v-btn>




    <v-btn height="10vh">
      <span>Present Now</span>

      <v-icon>mdi-television-play</v-icon>
    </v-btn>

    <v-btn height="10vh" @click="chat_drawer = true">
      <span>Chat</span>

      <v-icon>mdi-message-text</v-icon>
    </v-btn>

    <v-btn height="10vh">
      <span>Record</span>

      <v-icon>mdi-record-circle</v-icon>
    </v-btn>

    


    

    <v-btn color="error" style="position:absolute;right:0;height:10vh"><span>Exit</span><v-icon>mdi-logout</v-icon></v-btn>

    
  </v-bottom-navigation>


</main>
</template>

<script>
  export default {
    name: 'Home',
    data: () => ({
      benched: 0,
      chat_drawer:false,
      group_drawer:false,
      mic:true,
      video:true,
      model: 0,
      colors: [
        'primary',
        'secondary',
        'yellow darken-2',
        'red',
        'orange',
      ],
    }),
    computed: {
      items () {
        return Array.from({ length: this.length }, (k, v) => v + 1)
      },
      length () {
        return 7000
      },
  }
  }
</script>