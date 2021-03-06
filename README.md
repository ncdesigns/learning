@import "bourbon";

// ------------ START Boring stuff
@import url(https://fonts.googleapis.com/css?family=Lato);

$green: #2ea994;

body {
  font-family: 'Lato', Arial, sans-serif;
  background: #13171b;
  color: white;
  text-align: center;
}

.h1 {
    font-size: 30px;
}

// ------------ END Boring stuff

// ------------ START Fun stuff

.skills {
  list-style: none;
  font-size: 20px;
  padding: 0;
  .skill {
    display: block;
			    position: relative; // For positioning bar pseudo elements
			    height: 60px;
			    margin: 10px auto;
    width: 90%;
    @media only screen and (min-width: 900px) {
      display: inline-block;
			      width: percentage(1/4);
      margin: 10px;
    }
    &:before,
    &:after {
      content: "";
      position: absolute;
      border-radius: 20px;
      margin-top: 40px;
    }
    &:before {
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      height: 20px;
      background: #eeeeee;
    }
    &:after {
      background-color: $green;
      background: repeating-linear-gradient(-45deg, $green, $green 10px, lighten($green, 3) 10px, lighten($green, 3) 20px);
      height: 16px; 
      top: 2px;
      right: 95%;
      bottom: 2px;
      left: 2px;
      @include animation(fill 2s both);
    }
    @for $i from 1 through 5 {
      					&:nth-child(#{$i}):after {
          @include animation-delay(#{$i * 0.5}s);
      }
				    }
    &[aria-label="novice"]:after {
      right: 75%;
    }
    &[aria-label="average"]:after {
      right: 50%;
    }
    &[aria-label="adept"]:after {
      right: 35%;
    }
    &[aria-label="advanced"]:after {
      right: 20%;
    }
    &[aria-label="elite"]:after {
      right: 10%;
    }
    &[aria-label="pro"]:after {
      right: 2px;
    }
    &[aria-label="l33tasuar"]:after {
      // turn it up to 11!
      right: -10%;
    }
  }
}

@include keyframes(fill) {
  from {
    right: 100%;
  }
}

// ------------ END Fun stuff
