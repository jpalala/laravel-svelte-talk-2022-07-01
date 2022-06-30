<script>
  import logo from './assets/svelte.png'
	import NextPage from './NextPage.svelte';
	import PreviousPage from './PreviousPage.svelte';
	import { pageNum } from './stores.js';
	
  let page;
	let pageNumber;
	let imgWidth = 300;
	let imgHeight = 200;
	let slides = [
    "<h1>welcome</h1>", 
     "<p>I am this and that, I did this and that." , 
     "<p>Put whatever here and style using global styles</p>", 
     "<h3>End</h3>", 
     "<h1>Thank you!</h1><a href=\"mailto:email-address@example.com\">email-address at example.com</a>"   ];

	pageNum.subscribe(value => {
			
		pageNumber = value;
		const content = slides[value - 1];
		loadPage(content);
	});
	
	function loadPage(content) {
		if(content == undefined || content == null) {
			//alert("cant load it sorry");
		} else {
      let ewanpage = document.querySelector(".display");
			ewanpage.innerHTML = content;
		}
	}
</script>
<div class="header">
  <img src={logo} alt="Svelte Logo" width="80" height="80" />
</div>
<div id="full_page">
<div class="display"> innerHTML is the key.</div>
<div class="footer">

	<PreviousPage />
  <NextPage />

	{pageNumber}
	</div>
</div>

<style>
 :global(h1) {
     font-size: 3rem;
}
 :global(p) {
     font-size: 1.15rem;
     font-weight: 600;
}
 :global(b) {
     font-size: 1.5rem;
     font-weight: 900;
}
 :global(img.s){
     height: 52vh !important;
     width: 80vw;
     left: -15vw;
     top: -5vh;
     position: relative;
}
 :global(blockquote::before) {
     font-weight: bold;
     font-size: 1.3rem;
     content: "\201C \A";
}
 :global(blockquote::after) {
     font-weight: bold;
     font-size: 1.3rem;
     content: " \A \201D";
}
.header { 
  z-index: 100;
  width: 100%;
  position:absolute; 
  background: transparent;

}
.header img {
  height: 100px;
  left: 100px;
}
 #full_page {
     position: absolute;
     top: 0px;
     left: 5px;
     width: 100vw;
     height: 100vh;
     margin: 0.5rem;
     padding: 0;
     background: #111;
     color: white !important;
     display: flex;
}
/* this component inside can be the one that changes in svelte!! */
 #full_page .display {
     align-self: center;
     margin-left: 30vw;
}
 .footer {
     position:absolute;
     bottom: 0px;
     display: inline-block;
}
</style>

