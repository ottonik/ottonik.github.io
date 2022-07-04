<head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	<style>
		* {
			color: #fff;
			font-family: Arial, Helvetica, sans-serif;
		}
		body {
          background-image: url('7.jpg');
          background-repeat: no-repeat;
          background-attachment: fixed;
          background-size: 100% 100%;
        }
		.button {
			margin-top: 100px;
  			background-color: #00bfff; /* Green */
  			border: none;
			border-radius: 50px;
 			color: white;
  			padding: 15px 32px;
  			text-align: center;
  			text-decoration: none;
  			display: inline-block;
  			font-size: 60px;
			height:300px;
			width:500px;
			box-shadow: 0 0 12px 0 #000;
		}
		.input {
			height:300px;
			width:500px;

}
	</style>
<style type="text/css">@font-face { font-family: Roboto; src: url("chrome-extension://mcgbeeipkmelnpldkobichboakdfaeon/css/Roboto-Regular.ttf"); }</style></head>

<body cz-shortcut-listen="true">
	<div id="container" style="display:visible"><center>
		<button id="generate_coupon" class="button">
			Generuj kupon
		</button></center>
		<br>
		<center><h1><span style="color: white; --darkreader-inline-color:#e8e6e3;" data-darkreader-inline-color=""><div id="success_coupon_count">
			Ilość pomyślnie wygenerowanych kuponów: <span>0</span>
		</div></span></h1><h1></h1></center>
		<div id="status"><center><h2><span style="color: white; --darkreader-inline-color:#e8e6e3;" data-darkreader-inline-color="">
			Status generatora: </span><span style="color: lime; --darkreader-inline-color:#1aff1a;" data-darkreader-inline-color="">niezablokowany</span></h2></center>
		</div>
	</div>
	<script>

	const btn = document.getElementById('generate_coupon');
	btn.addEventListener('click', function onClick() {
	btn.style.backgroundColor = '#f00';
	btn.style.color = 'white';
	document.getElementById("generate_coupon").disabled = true;
	setTimeout(function(){
    btn.style.backgroundColor = '#00bfff';
    btn.style.color = 'white';
    document.getElementById("generate_coupon").disabled = false;
  }, 60000);
});

function data_handler(ev) {
  const button = document.getElementById('generate_coupon');
  const count = document.querySelector('#success_coupon_count > span');
  const status = document.querySelector('#status > span');
  if (!ev.success) {
    status.style.color = "red";
    status.innerText = "zablokowany";
    return button.setAttribute("disabled", "");
  };
  const iCount = parseInt(count.innerText) + 1;
  count.innerText = iCount;
  return cooldown_button(button, 20);
};

function click_handler() {
  const request = window.bridge.message("offerActivation");
  request.send({
    loyaltyId: 2400,
    autoActivate: false,
    offerId: 97983,
    offerInstanceId: 76afd968-ea43-42a5-ad9c-b979419fe8cc
  });
   request.on(data_handler, function (data) {
          console.log("offer activation data", loyaltyId, data);
        });
        request.on("error", function (error) {
          console.warn("MCD ERROR", loyaltyId, JSON.stringify(error));
        });
        request.on("done", function () {
          console.log("corn done 11", loyaltyId);
        });
};

function showPage(bridge) {
  window.bridge = bridge;
  document.getElementById("container").style.display = "block";
  document.getElementById('generate_coupon').addEventListener("click", click_handler);
};

document.addEventListener('mcdBridgeReady', () => {
  const { bridge } = window.mcd;
let user = mcd.bridge.message("user");
user.send({ promptlogin: true });
  return showPage(bridge);
});</script>
<script src="//cdn.jsdelivr.net/npm/eruda"></script>
    <script>
      eruda.init();
    </script>



</body>
