# HTML60秒倒计时

```markup
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>60秒倒计时</title>
</head>

<body>
    <input type="button" id="btn" value="获取验证码" onclick="sendemail()" />
</body>

</html>
<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script>
var countdown = 5

function sendemail() {
    var obj = $("#btn")
    settime(obj)
    console.log('发送邮件')
}

function settime(obj) {
    if (countdown == 0) {
        obj.attr('disabled', false)
        obj.val("获取验证码")
        countdown = 5
        return
    } else {
        obj.attr('disabled', true)
        obj.val("重新发送(" + countdown + ")")
        countdown--
    }
    setTimeout(function() {
        settime(obj)
    }, 1000)
}
</script>
```

