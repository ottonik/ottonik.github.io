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
        <img src="https://i.imgur.com/sgQXzaw.png" width="100" height="100" alt="" />
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
            }, 2500);
        });
        document.querySelector(".napierdalacz-stop").addEventListener("click", () => {
            if (intid) clearInterval(intid);
        });
        document.addEventListener("mcdBridgeReady", function (e) {
            console.log(mcd);
            console.log(JSON.stringify(mcd));
            console.log(mcd.bridge);
            console.log(JSON.stringify(mcd.bridge));
            console.log(typeof mcd);
            console.log(typeof mcd.bridge);
            console.log("gowno");
            let offerActivation = mcd.bridge.message("offerActivation");
            let deals = mcd.bridge.message("deals");
            let user = mcd.bridge.message("user");
            user.send({
            promptlogin: true
            });
            user.on("data", function (data) {
                console.log("chuj");
                console.log(data);
           console.log("chuj");
                console.log(typeof data);
           console.log("chuj");
                console.log(typeof mcd);
           console.log("chuj");
                console.log(typeof mcd.bridge);
          console.log("cycki1");
         console.log(JSON.stringify(loyaltyId));
        console.log("cycki");
        console.log(loyaltyId);
                console.log("chuj");
           console.log("chuj");
                console.log(JSON.stringify(loyaltyCardType));
           console.log("chuj");
           console.log("chuj");
                console.log(JSON.stringify(code));
           console.log("chuj");
                console.log(JSON.stringify(giftId));
           console.log("chuj");
                console.log(JSON.stringify(instanceId));
           console.log("chuj");
                console.log(JSON.stringify(redeemedOfferId));
           console.log("chuj");
                console.log(JSON.stringify(giftId));
           console.log("chuj");
        console.log("chuj");
                //   getPrize(offerActivation);
                let i = 985;
            });
            user.on("error", function (error) {});
            user.on("done", function () {});
        });
        function getPrize(bridge, loyalityId) {

            let couponId = coupons[Math.floor(Math.random() * coupons.length) + 1 - 1];
            let offerActivation = bridge.message("offerActivation")
            let offers = bridge.message("offers")
            offers.send({
            getRedeemedOffers: true
            });
            offerActivation.send({
                autoActivate: false,
                rewardId: 75980
            });
            offerActivation.on("data", function (data) {
                console.log("offer activation data", loyalityId, data[0]);
                console.log(JSON.stringify(data));
                console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
            offerActivation.on("error", function (error) {
                console.warn("MCD ERROR", loyalityId, JSON.stringify(error));
                console.log(JSON.stringify(loyaltyId));
            console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
            offerActivation.on("done", function () {
                console.log("corn done 11", loyalityId);
                console.log(offers);
            console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
            offers.on("data", function (data) {
                console.log("offers data", loyalityId, data);
                console.log(JSON.stringify(data));
            console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
            offers.on("error", function (error) {
                console.warn("offers MCD ERROR", loyalityId, JSON.stringify(error));
            console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
            offers.on("done", function () {
                console.log("offers done 22", loyalityId);
            console.log(loyaltyId),
               console.log(JSON.stringify(loyaltyId));
            });
        }
    </script>
    <script src="//cdn.jsdelivr.net/npm/eruda"></script>
    <script>
        eruda.init();
    </script>
</body>
</html>
