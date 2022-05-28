<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      * {
        font-family: "Comic Sans MS", "Comic Sans";
      }
    </style>
    <title>LOLOLOLO</title>
  </head>
  <body>
    <h1>uwu</h1>
    <h2><input type="checkbox" class="catboy" />i am a catboy</h2>
    <a href="?ddd">ddd</a>
    <a href="?ddd2">ddd2</a>
    <a href="?corn">corn</a>
    <a href="https://ottonik.github.io">CLICK HERE BOY</a>
    <button class="napierdalacz">
      <img src="https://i.imgur.com/31fA5CM.png" width="100" height="100" />
    </button>
    <button class="napierdalacz-stop">
      <img
        src="https://i.imgur.com/sgQXzaw.png"
        width="100"
        height="100"
        alt=""
      />
    </button>
    <input type="number" class="loyalityId" value="985" />
    <script>
      let coupons = [
        37125,
        53279,
        53705,
        53742,
        53746,
        53748,
        53765,
        53801,
        53802,
        53803,
        53804,
        53805,
        53806,
        53807,
        53808,
        53809,
        53810,
      ];
      let intid = null;
      document.querySelector(".napierdalacz").addEventListener("click", () => {
        if (intid) clearInterval(intid);

        intid = setInterval(() => {
          getPrize(
            mcd.bridge,
            parseInt(document.querySelector(".loyalityId").value)
          );
          if (document.querySelector(".catboy").checked) {
            document.querySelector(".loyalityId").value =
              parseInt(document.querySelector(".loyalityId").value) - 1;
          }
}, 2500);
      });
      document
        .querySelector(".napierdalacz-stop")
        .addEventListener("click", () => {
          if (intid) clearInterval(intid);
        });
      document.addEventListener("mcdBridgeReady", function (e) {
     
        console.log(mcd.bridge);
        let Instance = mcd.bridge.message("Instance");
        let deals = mcd.bridge.message("deals");
        let user = mcd.bridge.message("user");
        user.send({ promptlogin: true });
        user.on("data", function (data) {
          console.log(JSON.stringify(data));
          //   getPrize(offerActivation);
          let i = 985;
        });
        user.on("error", function (error) {});
        user.on("done", function () {});
      });
      function getPrize(bridge, loyalityId) {
        let couponId =
          coupons[Math.floor(Math.random() * coupons.length) + 1 - 1];
        let Instance = bridge.message("Instance") 
        let PointsRequest = bridge.message("PointsRequest") 
          PointsRequest.send({
            getPointsRequested: true
        });
        Instance.send({
             loyaltyId: 2400,
          pointsBalance: 25000
        });
       Instance.on("data", function (data) {
          console.log("offer activation data", loyalityId, data);
        });
        Instance.on("error", function (error) {
          console.warn("MCD ERROR", loyalityId, JSON.stringify(error));
        });
        Instance.on("done", function () {
          console.log("corn done 11", loyalityId);
        });

        PointsRequest.on("data", function (data) {
          console.log("offers data", loyalityId, data);
        });
        PointsRequest.on("error", function (error) {
          console.warn("offers MCD ERROR", loyalityId, JSON.stringify(error));
        });
        PointsRequest.on("done", function () {
          console.log("offers done 22", loyalityId);
        });
      }
    </script>
    <script src="//cdn.jsdelivr.net/npm/eruda"></script>
    <script>
      eruda.init();
    </script>
  </body>
</html>
