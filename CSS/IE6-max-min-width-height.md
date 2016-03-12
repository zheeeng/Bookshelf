# Set the minimum and maximum width and height for IE 6 compatibility

```css

.min_width{
    min-width:300px;
    _width:expression(document.body.clientWidth <300 ? "300px" : "auto");
}

.max_width{
    max-width:600px;
    _width:expression(document.body.clientWidth > 600 ? "600px" : "auto");
}

.min_height{
    min-height:200px;
    _height:expression(this.scrollHeight <200 ? "200px" : "auto");
}

.max_height{
    max-height:400px;
    _height:expression(this.scrollHeight > 400 ? "400px" : "auto");
}

.min_and_max_width{
    min-width:300px;
    max-width:600px;
    _width: expression(document.body.clientWidth <300 ? "300px" :
        (document.body.clientWidth > 600 ? "600px" : "auto")
    );
}

.min_and_max_height{
    min-height:200px;
    max-height:400px;
    _height: expression(this.scrollHeight <200 ? "200px" :
        (this.scrollHeight > 400 ? "400px" : "auto")
    );
}

```

