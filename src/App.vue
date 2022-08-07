<template>
  <div id=app>
    <header>
    <h1>TABS &nbsp;<span>ACCORDION</span></h1>
    </header>
    <div class="faqs">
      <FAQ 
      v-for="(faq, i) in faqs" 
      :faq="faq" 
      :index="i" 
      :key="i"
      :open="faq.open"
      @toggleOpen="toggleOpen"
      />
     
    </div>
  </div>
</template>

<script>
import FAQ from './FAQ';

export default {
  name: 'App',
  components: {
    FAQ
  },
  data () {
    return{
      faqs: [
        {
          title:"Section 1",
          content:"Maecenas nec semper ante, pellentesque posuere lorem. Nullam ipsum massa, consequat eget urna ut, pulvinar dignissim lorem. Nulla facilisi. Nam mattis eleifend metus. Fusce at commodo lorem. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Phasellus pellentesque elit sem, vel blandit posuere.",
          open: false
        },

        {
          title:"Section 2",
          content:"Mauris a orci sodales, scelerisque velit vitae, gravida nisl. Ut non laoreet eros, vel laoreet nisi. Praesent sed dolor dui. Proin non fringilla quam. Aliquam erat volutpat. Vestibulum vel arcu semper, lobortis turpis ac, ultricies nisi. Praesent id.",
          open: false
        },

        {
          title:"Section 3",
          content:"Sed elementum sapien ut sapien imperdiet, eu venenatis enim rhoncus. Praesent euismod tincidunt rhoncus. Duis cras amet",
          open: false
        },
        {
          title:"Section 4",
          content:"Cras dictum. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Aenean lacinia mauris vel est. Suspendisse eu nisl. Nullam ut libero. Integer dignissim consequat lectus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.",
          open: false
        },
  
      ]
    }
  },
  methods : {
    toggleOpen: function (index){
      this.faqs = this.faqs.map((faq, i) => {
        if (index === i) {
          faq.open = !faq.open;
        } else {
          faq.open = false;
        }

        return faq;
      }); 
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #EEE;
  font-family: sans-serif;
}

header{
  background-color: #3c3c3c;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
}

header h1{
  color: #EEE;
  font-size:28px;
  font-weight: 300;
  text-transform: uppercase;
}


header h1 span {
  color:#56E3B8;
  font-weight: 900;
}

.faq {
  display: block;
  width:100%;
  max-width:768px;
  margin:15px auto;
  padding:15px;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0,0,0,0.2);
  background-color: #FFF;
}

.faq .sec {
  position: relative;
  color:#3c3c3c;
  font-size: 20px;
  transition: all 0.4s linear;
}


.faq .sec::after {
  content: '';

  position: absolute;
  top: 50%;
  right: 0px;
  transform: translateY(-50%) rotate(0deg);

  width: 30px;
  height: 30px;
  background-image: url('./arrow-down-3101.svg');
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;

  transition: all 0.2s linear;
 
}
.faq.open .question{
  margin-bottom: 15px;
}

.faq.open .sec::after {
  transform: translateY(-50%) rotate(90deg);
}

.faq .content{
 color: #3c3c3c;
 font-size: 18px;
 opacity: 0;
 max-height: 0px;
 overflow-y: hidden;
 transition: all 0.4s ease-out;
}

.faq.open .content{
  opacity: 1;
  max-height: 1000px;
}
</style>
