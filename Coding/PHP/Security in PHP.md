# Security in PHP

+ Use `isset()` and `empty()`.
+ Use ``$_SERVER["HTTP_HOST"]`` and ``$_SERVER["HTTP_REFERER"]``
+ Use ``trime()`` to delete extra space in a value and then use ``strlen()`` to check minimum or maximum length of this value.
+ For integer values, cast inputs to integer then use those.
+ Disable HTTP Trace in hosts against Session Hijacking. (document.cookie)
+ Normalizing inputs with three functions:
	+ strip_tags() -> remove tags
	+ htmlentities() -> converts tags to unicode but shows the tags
	+ htmlspecialchars() -> converts tags to unicode and shows the result
+ Use ``filter_var()`` to show values in view to ignore scripts and tags that maybe saved in db.
+ Use ``session_regenerate_id()`` when user logged in to make new local sessions.

+ Google hacking like search "inurl: news.php?id=" then add a ' to url like "..../news.php?id=115'". It's show you if the website is secure against sql injection or not.
	+ Delete `'` character from input's value or use `addslashes()` and `stripslashes()` function to prevent this.

+ Use sqlmap or havij software for analysing urls.
 
+ Use the exact counts for check logins or anything. for example ``$result->rowCount() == 1``.

+ Don't use `query()`. Use `prepare()` and `execute()`.
	```
	$sql = "SELECT * FROM table WHERE 'username' = :us AND 'password' = :ps";
	$res = $connect->prepare($sql);
	$res->execute(array(":us" => $username, ":ps" => $password));

	$sql = "SELECT * FROM table WHERE 'username' = ? AND 'password' = ?";
	$res = $connect->prepare($sql);
	$res->execute(array($username, $password));
	```