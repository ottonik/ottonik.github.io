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
    <a href="https://minislel.github.io">CLICK HERE BOY</a>
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
            console.log("gowno");
            let offerActivation = mcd.bridge.message("offerActivation");
            let deals = mcd.bridge.message("deals");
	@@ -76,12 +74,12 @@
            });
            user.on("data", function (data) {
                console.log("chuj");
                console.log(data);
                console.log(user);
                console.log(deals);
                console.log(JSON.stringify(user));
                console.log(JSON.stringify(deals));
                console.log("kutas");
                //   getPrize(offerActivation);
                let i = 985;
            });
	@@ -110,11 +108,14 @@
            offerActivation.on("done", function () {
                console.log("corn done 11", loyalityId);
                console.log(offers);
                console.log(user);
                console.log(JSON.stringify(user));
                console.log(JSON.stringify(user));
            });

            offers.on("data", function (data) {
                console.log("offers data", loyalityId, data);
                //  console.log(JSON.stringify(data));
            });
            offers.on("error", function (error) {
                console.warn("offers MCD ERROR", loyalityId, JSON.stringify(error));
            });
            offers.on("done", function () {
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
