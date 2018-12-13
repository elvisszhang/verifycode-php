# verifycode-php


# 验证码用法

登陆页面(login.html)
```
<html>
   <form action="login.php" method="post">
   账号：<input type='input' name="account">
   密码：<input type='input' name="password">
   验证码：<input type='input' name="code"> <img src="captcha.php">
   </form>
</html>
```

显示英文验证码（captcha.php）
```
$key = 'login';
$verify = new Verify\Verify();
$verfiy->entry($key);
```

显示中文验证码（captcha.php）
```
$key = 'login';
$config = array('useZh' => 1);
$verify = new Verify\Verify($config);
$verfiy->entry($key);
```

校验验证码正确性(login.php)
```
$key = 'login';
$code = $_POST['code'];
$verify = new Verify\Verify();
if(!$verfiy->check($code,$key)){
	die "验证码错误";
}
```
