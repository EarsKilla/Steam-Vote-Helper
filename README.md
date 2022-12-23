# Steam vote helper

This version will work only with `THE STEAM AWARDS`. 2022 year.

1. Just open your favourite browser
2. Navigate [here](https://store.steampowered.com/steamawards) and login if not yet logged in
3. Open browser console (in most browsers it should be `F12` key on your keyboard)
4. Copy following code to browser console and press `Enter`  
```js
let sessionId = WebStorage.GetCookie("sessionid");
let isAccountLimited = false;

function OnAppVoteClick(voteid, appid, developerid) {
  if (isAccountLimited) {
    return;
  }
  $J.post("https://store.steampowered.com/salevote", {
    sessionid: sessionId,
    voteid: voteid,
    appid: appid,
    developerid: developerid,
  })
    .done(function (data) {
      if (data.startsWith("Ваш аккаунт не отвечает") || data.startsWith("Your account does")) {
        console.error("account limited");
        isAccountLimited = true;
      } else {
        console.info("Vote for " + appid + " was succeed");
      }
    })
    .fail(function () {
      console.error("Vote for " + appid + " was FAILED");
    });
}
OnAppVoteClick("72", "1245620", "0");
OnAppVoteClick("73", "1659040", "0");
OnAppVoteClick("74", "275850", "0");
OnAppVoteClick("75", "1938090", "0");
OnAppVoteClick("76", "1063660", "0");
OnAppVoteClick("77", "261550", "0");
OnAppVoteClick("78", "1811260", "0");
OnAppVoteClick("79", "1761390", "0");
OnAppVoteClick("80", "1593500", "0");
OnAppVoteClick("81", "920210", "0");
OnAppVoteClick("82", "1997040", "0");
```

---

Output will be like this:  
![output image](sample_output.png)

# Something like license
You're all free to copy, distribute, edit and do what you want with this but leave credits.
