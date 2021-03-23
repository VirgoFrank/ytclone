<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      permanent
      app
      :clipped="clipped"
      :mini-variant.sync="mini"
      v-bind:width="55"
    >
      <v-list dense class="pb-0">
        <v-list-item v-for="item in First3options" :key="item.title" link>
          <v-list-item-icon class="mb-5">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
        </v-list-item>
      </v-list>
      <v-list dense class="pt-0">
        <v-list-item v-for="item in items2" :key="item.title" link>
          <v-list-item-icon class="mb-5">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer
      class="v-navigation-drawercontent"
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in First3options"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list>
        <v-list-item
          v-for="(item, i) in items2"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <p class="subtitle-2" style="margin: 15px 10px 15px 30px">
        Sign in to like videos, comment, and subscribe.
      </p>
      <img class="ml-5" src="../assets/sign_in.png" />
      <v-divider></v-divider>
      <p class="subtitle-2 grey--text" style="margin: 15px 10px 0 30px">
        BEST OF YOUTUBE
      </p>
      <v-list>
        <v-list-item
          v-for="(item, i) in items3"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-img
              max-height="30"
              max-width="30"
              v-bind:src="item.icon"
            ></v-img>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list>
        <v-list-item
          v-for="(item, i) in items4"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <p
        v-if="!miniVariant"
        class="subtitle-2 grey--text"
        style="margin: 15px 10px 0 30px"
      >
        MORE FROM YOUTUBE
      </p>
      <v-list>
        <v-list-item
          v-for="(item, i) in items5"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list>
        <v-list-item
          v-for="(item, i) in items6"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action class="ml-2">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="body-2" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-divider></v-divider>
      <div class="ml-6 mr-7 mt-1" style="letter">
        <a class="text--secondary caption">About</a>
        <a class="text--secondary caption">Press</a>
        <a class="text--secondary caption">Copyright</a>
        <a class="text--secondary caption">Contact us</a>
        <a class="text--secondary caption">Creators</a>
        <a class="text--secondary caption">Advertise</a>
        <a class="text--secondary caption">Developers</a>
      </div>
      <div class="ml-6 mr-8 mt-2">
        <a class="text--secondary caption">Terms</a>
        <a class="text--secondary caption">Privacy</a>
        <a class="text--secondary caption">Policy & Safety</a>
        <a class="text--secondary caption">How Youtube works</a>
        <a class="text--secondary caption">Test new features</a>
      </div>
    </v-navigation-drawer>

    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-img
        max-height="50"
        max-width="110"
        src="https://upload.wikimedia.org/wikipedia/commons/e/e1/Logo_of_YouTube_%282015-2017%29.svg"
      ></v-img>
      <v-spacer />
      <v-container>
        <v-row justify="center">
          <input
            class="white--text"
            style="width: 40%; background-color: black"
            type="text"
            placeholder="Search"
          />
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="search-bar--button grey--text darken-3 grey rounded-0"
                v-bind="attrs"
                v-on="on"
              >
                <v-icon>mdi-magnify</v-icon>
              </v-btn>
            </template>
            <span>Search</span>
          </v-tooltip>
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-icon class="ml-4" v-bind="attrs" v-on="on">
                mdi-microphone
              </v-icon>
            </template>
            <span>Search with your voice</span>
          </v-tooltip>
        </v-row>
      </v-container>
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-icon class="mr-8" v-bind="attrs" v-on="on"> mdi-apps </v-icon>
        </template>
        <span>Youtube apps</span>
      </v-tooltip>
      <v-menu max-width="400px" offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-icon class="mr-8" rounded v-bind="attrs" v-on="on">
            mdi-dots-vertical
          </v-icon>
        </template>
        <v-list class="pt-0 pb-0">
          <v-list-item
            v-for="(item, i) in Settings"
            :key="i"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action class="ml-2">
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="body-2" v-text="item.title" />
            </v-list-item-content>
             <v-icon v-if="i < 3">{{"mdi-chevron-right"}}</v-icon>
          </v-list-item>
        </v-list>
        <v-divider></v-divider>
        <v-list class="pt-0 pb-0">
          <v-list-item 
            v-for="(item, i) in Mode"
            :key="i"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action class="ml-2 mr-0 pr-0" style="margin: 0 0 0 0">
              <v-list-item-title class="body-2 pr-10" v-text="item.title" />
            </v-list-item-action>
            <v-list-item-content >
              
            </v-list-item-content>
            <v-icon >{{"mdi-chevron-right"}}</v-icon>
          </v-list-item>
        </v-list>
      </v-menu>
      <img src="../assets/sign_in.png" />
    </v-app-bar>
    

    <v-main class="grey darken-4">
      <v-container>
        <v-row class="ml-100" style="margin-left: 20px; margin-right: 50px; padding-bottom:10px">
          <template v-for="n in 1" >
            <v-col
              :key="n"
              class="mt-2 "
              cols="12"
            >
              <!-- <strong>Category {{ n }}</strong> -->
            </v-col>

            <v-col
              v-for="j in videos"
              :key="`${n}${j}`"
              cols="4"
              md="3"
              style="padding-bottom:130px"
            >
              <v-sheet height="230" class="pl-4 pb-10">
                <v-row>
                <v-img height="240" :src="j.thumbnail"></v-img>
                </v-row>
                <v-row>
                <v-avatar size="40" class="mt-3">
                  <v-img :src="j.thumbnail"></v-img>
                </v-avatar>
              <v-list-item-content>
                <v-list-item-title class="body-3 pl-3 pb-1" style="font-size: 18px;" v-text="j.title" />
                <div class="pl-3">
                  <p style="margin-bottom: 0; font-size:15px">{{j.channel}}</p>
                  <p style="margin-bottom: 0; font-size:15px">{{j.views}} • {{j.uploadDate}}</p>
                </div>
  
              </v-list-item-content>
                </v-row>
              </v-sheet>
            </v-col>
          </template>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
  
</template>

<style >
::-webkit-scrollbar {
  width: 10px;
}
</style>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      miniVariant: false,
      right: true,
      rightDrawer: false,
      videos:[
        {title:"Soop Dogg Goes to High Hrothgar", channel:"Happydeathgrin", views:"96M views", uploadDate:"10 years ago", thumbnail:"http://i3.ytimg.com/vi/AYwAyNcwLQg/maxresdefault.jpg", avatar:""},
        {title:`OFFICIAL - Somewhere Over the Rainbow 2011 - Israel "IZ" Kamakawiwo'ole by Mountain Apple Company Inc`, channel:"Mountain Apple Company Inc", views:"96M views", uploadDate:"10 years ago", thumbnail:"http://i3.ytimg.com/vi/w_DKWlrA24k/hqdefault.jpg", avatar:""},
        {title:`Dagoth Ur is at Your Door`, channel:"Micky D", views:"72K views", uploadDate:"1 day ago", thumbnail:"http://i3.ytimg.com/vi/ILAzFQODFBo/maxresdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
        {title:`Booting MS DOS 1.0 on old Compaq PC`, channel:"Rene Therunbiker", views:"42K views", uploadDate:"1 year ago", thumbnail:"http://i3.ytimg.com/vi/0-X7Thsn0pI/hqdefault.jpg", avatar:""},
      ],
      images: {
        url: "@sign_in.png",
      },
      Mode:[
        {icon:"", title:"Restricted Mode: Off", to:"/"},
      ],
      Settings: [
        { icon: "mdi-brightness-4", title: "Appearance: Dark", to: "/" },
        { icon: "mdi-translate", title: "Language: English", to: "/" },
        { icon: "mdi-web", title: "Location: Estonia", to: "/" },
        { icon: "mdi-cog", title: "Settings", to: "/" },
        { icon: "mdi-shield-account", title: "Your data in Youtube", to: "/" },
        { icon: "mdi-help-circle", title: "Help", to: "/" },
        { icon: "mdi-message-alert", title: "Send feedback", to: "/" },
        { icon: "mdi-keyboard", title: "Keyboard shortcuts", to: "/" },
      ],
      First3options: [
        { icon: "mdi-home", title: "Home", to: "/" },
        { icon: "mdi-compass", title: "Explore", to: "/1" },
        { icon: "mdi-youtube-subscription", title: "Subscriptions", to: "/2" },
      ],
      items2: [
        { title: "Library", icon: "mdi-play-box-multiple", to: "/3" },
        { title: "History", icon: "mdi-history", to: "/4" },
      ],
      items3: [
        {
          title: "Music",
          icon:
            "https://yt3.ggpht.com/fa4T1dRmZJIGyq3wRJaO69jra1qYqS9nuXgGJWLbENRfHnRw1igVUJ__iRXqeIUinYTBvEMBljM=s88-c-k-c0x00ffffff-no-rj",
          to: "/5",
        },
        {
          title: "Sports",
          icon:
            "https://yt3.ggpht.com/okIrV-Ysg5GkAJwjsSl5KChZIlcw7chFfpeYqXeBHzLBBNjipqnLax3WUnjGRrArs3Fq8g7GJQ=s88-c-k-c0x00ffffff-no-rj",
          to: "/6",
        },
        {
          title: "Gaming",
          icon:
            "https://yt3.ggpht.com/e-xctNLUqrlggKDMfPKioMjp5-1wVrMsATnIQgliz6GQ0-rm6ZxbO-WN3Ts5kUXX2HEuN6fnjQ=s88-c-k-c0x00ffffff-no-rj",
          to: "/7",
        },
        {
          title: "News",
          icon:
            "https://yt3.ggpht.com/OJyV7XWydLP9ojx1HhHwcvd5vu3y3DKdzkVxC2KePh8bGhfs2APepWUwgKpQpYJrjnr8xHQaBw=s88-c-k-c0x00ffffff-no-rj",
          to: "/8",
        },
        {
          title: "Live",
          icon:
            "https://yt3.ggpht.com/8D6JlsnvwDZFMdcbjqVji82kggP3aXXbO-yBD0RFrKlp4G1zNt9wcqcVTSPnAI8GuUAbDYQwsg=s88-c-k-c0x00ffffff-no-rj",
          to: "/9",
        },
        {
          title: "360 Video",
          icon:
            "https://yt3.ggpht.com/AXGh2eLc-9P1-_QmNz3eTAN-3EQI-K-k2_PqgCH2pBYPvpe9H3AIgqeQrw7yeQLZW3Bld-ppvA=s88-c-k-c0x00ffffff-no-rj",
          to: "/10",
        },
      ],
      items4: [
        { title: "Browse channels", icon: "mdi-plus-circle", to: "/11" },
      ],
      items5: [
        { title: "Youtube Premium", icon: "mdi-youtube", to: "/12" },
        { title: "Live", icon: "mdi-access-point", to: "/13" },
      ],
      items6: [
        { title: "Settings", icon: "mdi-cog", to: "/14" },
        { title: "Report history", icon: "mdi-flag", to: "/15" },
        { title: "Help", icon: "mdi-help-circle", to: "/16" },
        { title: "Send feedback", icon: "mdi-message-alert", to: "/17" },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "",
    };
  },
};
</script>
