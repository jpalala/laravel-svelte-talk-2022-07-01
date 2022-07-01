<script>
  import logo from './assets/svelte.png';
  const authMeIllustration = 'https://raw.githubusercontent.com/jpalala/laravel-svelte-talk-2022-07-01/main/src/assets/authenticate_me_illustration.jpeg';
	
  import NextPage from './NextPage.svelte';
  import PreviousPage from './PreviousPage.svelte';
  import { pageNum } from './stores.js';

  let page;
  let pageNumber;
  let imgWidth = 600;
  let imgHeight = 450;
  let slides = ["<h1>welcome</h1>",
    "<h3>Question?</h3><p>what are three ways you can pass authentication from backend to frontend?</p>",
    '<img src="' + authMeIllustration + '" alt="IMG-20220701-141332" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/PTGJ9yh/IMG-20220701-141405.jpg" alt="IMG-20220701-141405" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    "<b>HTTP is Stateless<b>", "<h3>What is a CSRF attack?</h3>",
    "<h3>Authentication: secure cookies, localStorage, and JWT</h3>", "<h3>Laravel Sanctum</h3>",
    "<blockquote>In Laravel, the CSRF cookie is used to verify that the authenticated user is the person actually making the requests to the application.</blockquote>",
    "<blockquote>In order to authenticate, your SPA and API must share the same top-level domain. However, they may be placed on different subdomains. Additionally, you should ensure that you send the <code>Accept: application/json</code> header with your request.</blockquote>",
    "<h3>You can also use JWT (in cookie or localstorage)!</h3>",
    "<p>All that matters is: after being authenticated, Laravel will take care of the sessions as long as the encrypted cookies it makes can check if the user is logged in or not</p>",
    '<img src="https://i.ibb.co/FxCk2rn/part-install-1.png" alt="part-install-1" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/0cGtf55/setup-cors-part-3.png" alt="setup-cors-part-3" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/T2s9m8y/setup-kernel-part-2.png" alt="setup-kernel-part-2" border="0" width="750" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/gvqNgZD/setup-sanctum-config-part-4.png" alt="setup-sanctum-config-part-4" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/tJM6sN2/setup-user-model-part-1-5.png" alt="setup-user-model-part-1-5" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/h7p3wr2/setup-controllers-a.png" alt="setup-controllers-a" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">',
    '<img src="https://i.ibb.co/LJ4zvKN/setup-controllers-b.png" alt="setup-controllers-b" border="0" width="' + imgWidth.toString() + '" height="' + imgHeight.toString() + '">>'
  ];

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
<div class="display">Getting Svelte and Laravel to Talk to Each Other</div>
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

