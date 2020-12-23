# Steam vote helper

This version will work only with `THE STEAM AWARDS`. 2020 year.

1. Just open your favourite browser
2. Navigate [here](https://store.steampowered.com/steamawards) and login if not yet logged in
3. Open browser console (in most browsers it should be `F12` key on your keyboard)
4. Copy following code to browser console and press `Enter`  
```js
function OnAppVoteClick(voteid, appid) {
	$J
	.post('https://store.steampowered.com/salevote', {sessionid: g_sessionID, voteid: voteid, appid: appid,  developerid: 0 })
	.done(function(data) {
		console.log('Vote ' + voteid + ' for ' + appid + ' was succeed');
	})
	.fail(function() {
		console.log('Vote ' + voteid + ' for ' + appid + ' was FAILED');
	}) 
};
OnAppVoteClick( '50', '1190460' );
OnAppVoteClick( '51', '1019550' );
OnAppVoteClick( '52', '275850' );
OnAppVoteClick( '53', '397540' );
OnAppVoteClick( '55', '1190460' );
OnAppVoteClick( '58', '1151640' );
OnAppVoteClick( '56', '1139900' );
OnAppVoteClick( '54', '1238810' );
OnAppVoteClick( '57', '782330' );
OnAppVoteClick( '59', '837470' );
```

---

Output will be like this:  
![output image](sample_output.png)

# Something like license
You're all free to copy, distribute, edit and do what you want with this but leave credits.
