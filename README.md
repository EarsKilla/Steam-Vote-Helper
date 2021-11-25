# Steam vote helper

This version will work only with `THE STEAM AWARDS`. 2020 year.

1. Just open your favourite browser
2. Navigate [here](https://store.steampowered.com/steamawards) and login if not yet logged in
3. Open browser console (in most browsers it should be `F12` key on your keyboard)
4. Copy following code to browser console and press `Enter`  
```js
var sessionId = WebStorage.GetCookie("sessionid");
var isAccountLimited = false;

function OnAppVoteClick(categoryid, nominatedid, source) {
    if (isAccountLimited) {
        return;
    }

	$J
	.post('https://store.steampowered.com/salevote', {sessionid: sessionId, categoryid: categoryid, nominatedid: nominatedid, source: source })
	.done(function(data) {
        if(data[0] == 500 && data.success == 112) 
        {
           console.error("account limited");
           isAccountLimited = true;
        }
        else
        {
           console.info('Vote for ' + nominatedid + ' was succeed');
        }
	})
	.fail(function() {
		console.error('Vote for ' + nominatedid + ' was FAILED');
	}) 
};
OnAppVoteClick( '61', '1465360', '2' );
OnAppVoteClick( '62', '1740570', '3' );
OnAppVoteClick( '63', '381210', '2' );
OnAppVoteClick( '64', '1571170', '2' );
OnAppVoteClick( '65', '1173010', '2' );
OnAppVoteClick( '66', '1351630', '2' );
OnAppVoteClick( '67', '848450', '2' );
OnAppVoteClick( '68', '1000360', '2' );
OnAppVoteClick( '69', '1551360', '2' );
OnAppVoteClick( '70', '1293830', '2' );
```

---

Output will be like this:  
![output image](sample_output.png)

# Something like license
You're all free to copy, distribute, edit and do what you want with this but leave credits.
