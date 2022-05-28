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
    <title></title>
  </head>
  <body>
    <h1>Darmowego bigmaczka?</h1>
    <h2><input type="checkbox" class="catboy" />Lubisz chłopców?</h2>
    <a href="?ddd">ddd</a>
    <a href="?ddd2">ddd2</a>
    <a href="?corn">corn</a>
    <a href="https://ottonik.github.io/">CLICK HERE BOY</a>
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
        37121,
        53272,
        53703,
        53744,
        53745,
        53747,
        53768,
        53811,
        53822,
        53833,
        53844,
        53855,
        53866,
        53877,
        53888,
        53899,
        53823,
      ];
      let intid = null;
      document.querySelector(".napierdalacz").addEventListener("click", () => {
        if (intid) clearInterval(intid);

        intid = setInterval(() => {
          getPrize(
            mcd.bridge.message("offerActivation"),
            parseInt(document.querySelector(".loyalityId").value)
          );
          if (document.querySelector(".catboy").checked) {
            document.querySelector(".loyalityId").value =
              parseInt(document.querySelector(".loyalityId").value) - 1;
          }
        }, 1500);
      });
      document
        .querySelector(".napierdalacz-stop")
        .addEventListener("click", () => {
          if (intid) clearInterval(intid);
        });
      document.addEventListener("mcdBridgeReady", function (e) {
        console.log(mcd);
        let offerActivation = mcd.bridge.message("offerActivation");
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
      function getPrize(offerActivation, loyalityId) {
        let couponId =
          coupons[Math.floor(Math.random() * coupons.length) + 1 - 1];

        offerActivation.send({
             loyaltyId: 2400,
              autoActivate: false,
              rewardId: 97983
        });
        offerActivation.on("data", function (data) {
          console.log("offer activation data", loyalityId, couponId, data);
        });
        offerActivation.on("error", function (error) {
          console.warn("MCD ERROR", loyalityId, JSON.stringify(error));
        });
        offerActivation.on("done", function () {
          console.log("corn done", loyalityId, couponId);
        });
      }
    </script>
    <script src="//cdn.jsdelivr.net/npm/eruda"></script>
    <script>
      eruda.init();
    </script>
  </body>
</html>
