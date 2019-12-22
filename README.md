# Steam vote helper

This version will work only with `THE STEAM AWARDS`. 2019 year.

1. Just open your favourite browser
2. Navigate [here](https://store.steampowered.com/) and login if not yet logged in
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
OnAppVoteClick( '34', '814380' );
OnAppVoteClick( '35', '620980' );
OnAppVoteClick( '36', '230410' );
OnAppVoteClick( '37', '632360' );
OnAppVoteClick( '38', '736260' );
OnAppVoteClick( '39', '752590' );
OnAppVoteClick( '40', '629760' );
OnAppVoteClick( '41', '683320' );
```

---

Output will be like this:
![output image](sample_output.png)