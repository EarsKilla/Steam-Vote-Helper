# Steam vote helper

This version will work only with `THE STEAM AWARDS`. 2021 year.

1. Just open your favourite browser
2. Navigate [here](https://store.steampowered.com/steamawards) and login if not yet logged in
3. Open browser console (in most browsers it should be `F12` key on your keyboard)
4. Copy following code to browser console and press `Enter`  
```js
var sessionId = WebStorage.GetCookie("sessionid");
var isAccountLimited = false;

function OnAppVoteClick(voteid, appid, source) {
    if (isAccountLimited) {
        return;
    }
    $J.post('https://store.steampowered.com/salevote', {
            sessionid: sessionId,
            voteid: voteid,
            appid: appid,
            source: source
        })
        .done(function(data) {
            if (data.startsWith("Ваш аккаунт не отвечает") || data.startsWith("Your account does")) {
                console.error("account limited");
                isAccountLimited = true;
            } else {
                console.info('Vote for ' + appid + ' was succeed');
            }
        })
        .fail(function() {
            console.error('Vote for ' + appid + ' was FAILED');
        })
};
OnAppVoteClick('61', '1091500', '2');
OnAppVoteClick('62', '1402320', '3');
OnAppVoteClick('63', '252490', '2');
OnAppVoteClick('64', '1240440', '2');
OnAppVoteClick('65', '860510', '2');
OnAppVoteClick('66', '1195290', '2');
OnAppVoteClick('67', '1325200', '2');
OnAppVoteClick('68', '1382330', '2');
OnAppVoteClick('69', '1196590', '2');
OnAppVoteClick('70', '1248130', '2');
```

---

Output will be like this:  
![output image](sample_output.png)

# Something like license
You're all free to copy, distribute, edit and do what you want with this but leave credits.
