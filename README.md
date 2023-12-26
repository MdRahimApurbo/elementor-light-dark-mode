Example One GSAP Code - Use this to make the entire site into dark mode automatically
<script>
    ;(function(){
let chck_if_gsap_loaded = setInterval(function(){
        const eleBuilder = document.querySelector('body').classList.contains("elementor-editor-active");
   if(window.gsap && window.ScrollTrigger && !eleBuilder){
        gsap.registerPlugin(ScrollTrigger);
        light_dark_mode();
        clearInterval(chck_if_gsap_loaded);
    }
}, 500);

function light_dark_mode(){

const darkmode = gsap.timeline({paused:true});

const tl = gsap.timeline();

tl.to('body', {backgroundColor: '#000', duration:0.2}); // Body Background color
tl.set(".change-logo img", { attr: { src: '' } }, "<"); // change logo
tl.set(".dm-toggle .elementor-icon i", {className:"+=fa fa-moon"}, "<"); // Change toggle mode icon
tl.set(".dm-toggle .elementor-icon", {color: '#fff', duration:0.2}, "<"); // Change toggle icon color
tl.to(".dm-menu .elementor-menu-toggle", {color: '#fff'}, "<");	// Mobile hamburger icon color
tl.to("svg", {fill: '#fff', duration:0.2}, "<"); // Change icon SVG color
tl.to("i", {color: '#fff', duration:0.2}, "<"); // Change icon i color
tl.to(".elementor-button", {backgroundColor: '#fff', duration:0.2}, "<"); // Change button background color
tl.to(".elementor-button", {borderColor: '#fff', duration:0.2}, "<"); // Change button border color
tl.to(".elementor-button span", {color: '#000', duration:0.2}, "<"); // Change button text color
tl.to("h1", {color: '#fff'}, "<"); // Change Text color
tl.to("h2", {color: '#fff'}, "<");
tl.to("h3", {color: '#fff'}, "<");
tl.to("h4", {color: '#fff'}, "<");
tl.to("p", {color: '#fff'}, "<");
tl.set("a", {color: '#fff'}, "<");
tl.set("span", {color: '#fff'}, "<");
tl.to("div", {color: '#fff'}, "<");

darkmode.add(tl);
const button = document.querySelector(".dm-toggle");

    const currentTheme = localStorage.getItem("theme")

         // If no theme preference in local storage, check for browser dark mode
        if (!currentTheme) {
            if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
                currentTheme = 'dark';
            } else {
                currentTheme = 'light';
            }
        }

     // Set the theme based on preference
    if(currentTheme === "dark"){
        darkmode.play();
        button.classList.add("darkmode");
    }

   button.addEventListener("click", () => {
     if (!button.classList.contains("darkmode")) {
            // Play Timeline
         darkmode.play();
         button.classList.toggle("darkmode");
         localStorage.setItem("theme", "dark")
         } else {
            // Reverse Timeline
        darkmode.reverse();
     		button.classList.toggle("darkmode");
     		localStorage.setItem("theme", "light")
	}
});

}

})();

</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/ScrollTrigger.min.js"></script>
Example two GSAP code - Use this to have more control over witch elements change into dark mode
<script>
    ;(function(){
let chck_if_gsap_loaded = setInterval(function(){
        const eleBuilder = document.querySelector('body').classList.contains("elementor-editor-active");
   if(window.gsap && window.ScrollTrigger && !eleBuilder){
        gsap.registerPlugin(ScrollTrigger);
        light_dark_mode();
        clearInterval(chck_if_gsap_loaded);
    }
}, 500);

function light_dark_mode(){

const darkmode = gsap.timeline({paused:true});

const tl = gsap.timeline();

tl.to('body', {backgroundColor: '#000', duration:0.2}); // Body Background color
tl.set(".change-logo img", { attr: { src: 'https://wordpress-634977-2991492.cloudwaysapps.com/wp-content/uploads/2022/12/logo-white.png' } }, "<"); // change logo
tl.set(".dm-toggle .elementor-icon i", {className:"+=fa fa-moon"}, "<"); // Change toggle mode icon
tl.set(".dm-toggle .elementor-icon", {color: '#fff', duration:0.2}, "<"); // Change toggle icon color
tl.to(".dm-menu .elementor-menu-toggle", {color: '#fff'}, "<");	// Mobile hamburger icon color
tl.to(".dm-icon svg", {fill: '#fff', duration:0.2}, "<"); // Change icon SVG color
tl.to(".dm-icon i", {color: '#fff', duration:0.2}, "<"); // Change icon i color
tl.to(".elementor-button", {backgroundColor: '#fff', duration:0.2}, "<"); // Change button background color
tl.to(".elementor-button", {borderColor: '#fff', duration:0.2}, "<"); // Change button border color
tl.to(".elementor-button span", {color: '#000', duration:0.2}, "<"); // Change button text color
tl.to(".dm-text h1", {color: '#fff'}, "<"); // Change Text color
tl.to(".dm-text h2", {color: '#fff'}, "<");
tl.to(".dm-text h3", {color: '#fff'}, "<");
tl.to(".dm-text h4", {color: '#fff'}, "<");
tl.to(".dm-text p", {color: '#fff'}, "<");
tl.set(".dm-text a", {color: '#fff'}, "<");
tl.set(".dm-text span", {color: '#fff'}, "<");	 // Specific Text color class
tl.to(".dm-text div", {color: '#fff'}, "<");

darkmode.add(tl);
const button = document.querySelector(".dm-toggle");

   button.addEventListener("click", () => {
     if (!button.classList.contains("darkmode")) {
            // Play Timeline
         darkmode.play();
         button.classList.toggle("darkmode");
         } else {
            // Reverse Timeline
        darkmode.reverse();
     		button.classList.toggle("darkmode");
	}
});

}

})();

</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.9.0/ScrollTrigger.min.js"></script>
Toggle Switch Logic
const toggleCheckbox = document.querySelector("#darkmode-checkbox");

			toggleCheckbox.addEventListener("click", () => {
  			if (!toggleCheckbox.checked) {
					// Play Timeline
    			darkmode.play();
  			} else {
    			// Reverse Timeline
    			darkmode.reverse();
  }

});
Toggle Switch HTML
<label class="switch">
  <input type="checkbox" id="darkmode-checkbox" checked>
  <span class="slider round"></span>
</label>
Toggle Switch CSS
selector .switch {
  position: relative;
  display: inline-block;
  width: 50px;
  height: 25px;
}

selector .switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

selector .slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: .4s;
  transition: .4s;
}

selector .slider:before {
  position: absolute;
  content: "";
  height: 18px;
  width: 18px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

selector input:checked + .slider {
  background-color: #5149ff;
}

selector input:focus + .slider {
  box-shadow: 0 0 1px #2196F3;
}

selector input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
selector .slider.round {
  border-radius: 34px;
}

selector .slider.round:before {
  border-radius: 50%;
}# elementor-light-dark-mode
