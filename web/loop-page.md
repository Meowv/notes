# HTML多图无缝循环翻页效果

```markup
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>多图无缝循环翻页效果</title>
    <style>
    * {
        margin: 0;
        padding: 0;
    }

    .carousel {
        width: 1000px;
        height: 500px;
        margin: 0 auto;
        overflow: hidden;
    }

    .carousel ul li {
        width: 1000px;
        height: 500px;
        list-style-type: none;
        float: left;
    }

    .carousel ul li a img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }
    </style>
</head>

<body>
    <div class="carousel">
        <ul>
            <li>
                <a href="#">
                    <img src="https://api.meowv.com/girl" alt="1">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="https://api.meowv.com/girl" alt="2">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="https://api.meowv.com/girl" alt="3">
                </a>
            </li>
        </ul>
    </div>
</body>

</html>
<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script>
var carousel = $('.carousel ul'),
    li = $('.carousel ul li');
carousel.css('width', li.width() * li.length);
setInterval(function() {
    carousel.animate({
        'marginLeft': -li.width()
    }, 500, function() {
        $(this).animate({ 'marginLeft': 0 }, 0)
            .find('li').eq(0).appendTo($(this));
    });
}, 3000);
</script>
```

