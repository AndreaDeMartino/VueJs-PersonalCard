<template>
  <div class="card">
    
    <div class="front-face">
      <div class="contents front">
        <p>{{ frontName | uppercase }}</p>
        <p class="bottom-bar">{{ frontSurname | uppercase}}</p>
        <span>Full Stack Web Developer</span>
      </div>
    </div>

    <div class="back-face">
      <div class="contents back">
        <h2>{{ backTitle | uppercase}}</h2>
        <span>Follow Me</span>
        <div class="icons">
          <a v-for="link in links" :key="link.url" :href="link.url">
            <i :class="link.class"></i>
          </a>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  // Data
  data() {
    return {
      links: [
        {
         url: 'https://codepen.io/andreademartino',
         class: 'fab fa-codepen',
        },
        {
         url: 'https://github.com/AndreaDeMartino',
         class: 'fab fa-github',
        },
        {
         url: 'https://www.linkedin.com/in/andrea-de-martino',
         class: 'fab fa-linkedin-in',
        },
      ],
      frontName: 'Andrea',
      frontSurname: 'De Martino',
      backTitle: 'Check My Code'
    }
  },
  // Filters
  filters : {
    uppercase(text) {
      return text.toUpperCase();
    }
  }
}
</script>

<style lang="scss" scoped>

  /****************************************************
  * Card Settings
  ****************************************************/

  .card, .front-face,
  .back-face, .contents {
    position: absolute;
  }

  .card {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: 400px;
    width: 290px;
    transform-style: preserve-3d;
    perspective: 1000px;

    // Card Hover
    &:hover > .front-face{
      transform: rotateY(-180deg); 
    }
    &:hover > .back-face{
      transform: rotateY(0deg);  
    }

    // Card Icons
    .icons { 
      margin: 10px 0; 
      i {
        color: #042f4b;
        background: white;
        font-size: 20px;
        height: 40px;
        width: 40px;
        border-radius: 50%;
        line-height: 40px;
        margin: 0 5px;
        cursor: pointer;
      }
    }

    // Card Faces Rules
    .front-face, 
    .back-face {
      height: 100%;
      width: 100%;
      text-align: center;
      background: linear-gradient(rgba(0, 0, 0, .2), rgba(0, 0, 0, .2)), url('../assets/bg.jpg');
      background-size: cover;
      background-position: center;
      border-radius: 10px;
      backface-visibility: hidden;
      transform-style: preserve-3d;
      transition: transform .7s cubic-bezier(.4, .2, .2, 1);
    }
    .back-face { 
      transform: rotateY(180deg);
      background: linear-gradient(45deg, #0e0e0e 0%, #5a5959 100%);
    }

    //Card Contents
    .contents {
      left: 0;
      top: 50%;
      width: 100%;
      perspective: 100px;
      transform: translateY(-50%) translateZ(60px) scale(.94);

      //FrontCard
      &.front{
        p {
          color: white;
          font-size: 28px;
          margin-bottom: 5px;
          &.bottom-bar::after{
            content: '';
            display: block;
            left: 0;
            right: 0;
            height: 2px;
            width: 150px;
            background: white;
            margin: 0 auto;
            margin-top: 10px;
            margin-bottom: 20px;
          }
        }
        span {
          color: white;
          font-size: 12px;
          font-weight: 300;
        }
      }

      //BackCard
      &.back{
        color: white;
        h2 {
          font-size: 28px;
          margin-bottom: 10px;
          font-weight: 300;
        }
        span { 
          font-weight: 300;
          font-size: 12px;
        }
      }
    } 
  }

</style>