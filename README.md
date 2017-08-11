# jQuery带微信的返回顶部/底部代码scrollTop2
效果如下：

![](images/img.gif)
css code:
```
@charset "utf-8";
	/* CSS Document */
body {
	font-size:12px;
	font-family:"宋体";
	margin:0;
	padding:0;
	_background-image:url(text.txt);
	/* for IE6 */ _background-attachment:fixed;
}
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,p,blockquote,th,td {
	margin:0;
	padding:0;
}
a {
	color:#666;
	text-decoration:none;
}
a:hover {
	color:#1e90ff;
}
/* 浮动面板 */
#floatPanel {
	}#floatPanel .ctrolPanel {
	width:36px;
	height:166px;
	background:#fff url(../images/float-panel-bg.gif) no-repeat left top;
	border:solid 1px #ddd;
	position:fixed;
	right:25px;
	top:300px;
	overflow:hidden;
	z-index:10000;
	_position:absolute;
	/* for IE6 */_top:expression(documentElement.scrollTop + 300);
}
#floatPanel .ctrolPanel a {
	width:34px;
	font-size:12px;
	color:#ff6600;
	letter-spacing:1px;
	text-align:center;
	overflow:hidden;
}
#floatPanel .ctrolPanel .arrow {
	height:29px;
	line-height:28px;
	display:block;
	margin:1px auto;
}
#floatPanel .ctrolPanel .arrow span {
	display:none;
}
#floatPanel .ctrolPanel .arrow:hover {
	background:#f4f4f4;
}
#floatPanel .ctrolPanel .arrow:hover span {
	display:block;
}
#floatPanel .ctrolPanel .contact {
	height:60px;
	display:block;
	margin:2px auto;
}
#floatPanel .ctrolPanel .contact span {
	line-height:90px;
}
#floatPanel .ctrolPanel .qrcode {
	height:40px;
	display:block;
	margin:2px auto;
}
#floatPanel .ctrolPanel .qrcode span {
	display:none;
}
#floatPanel .popPanel {
	width:230px;
	height:242px;
	position:fixed;
	right:70px;
	top:300px;
	z-index:10000;
	overflow:hidden;
	display:none;
	_position:absolute;
	/* for IE6 */_top:expression(documentElement.scrollTop + 300);
}
#floatPanel .popPanel .popPanel-inner {
	width:230px;
	height:242px;
	position:relative;
	overflow:hidden;
}
#floatPanel .popPanel .popPanel-inner .arrowPanel {
	width:10px;
	height:240px;
	position:absolute;
	right:1px;
	top:102px;
}
#floatPanel .popPanel .popPanel-inner .arrowPanel .arrow01 {
	width:0;
	height:0;
	font-size:0;
	line-height:0;
	border-top:10px solid transparent;
	_border-top:10px solid black;
	_filter:chroma(color=black);
	border-right:10px solid transparent;
	_border-right:10px solid black;
	_filter:chroma(color=black);
	border-bottom:10px solid transparent;
	_border-bottom:10px solid black;
	_filter:chroma(color=black);
	border-left:10px solid #ddd;
	position:absolute;
	bottom:0;
	position:absolute;
	left:2px;
	top:0;
}
#floatPanel .popPanel .popPanel-inner .arrowPanel .arrow02 {
	width:0;
	height:0;
	font-size:0;
	line-height:0;
	border-top:10px solid transparent;
	_border-top:10px solid black;
	_filter:chroma(color=black);
	border-right:10px solid transparent;
	_border-right:10px solid black;
	_filter:chroma(color=black);
	border-bottom:10px solid transparent;
	_border-bottom:10px solid black;
	_filter:chroma(color=black);
	border-left:10px solid #fff;
	position:absolute;
	bottom:0;
	position:absolute;
	left:0;
	top:0;
}
#floatPanel .popPanel .popPanel-inner .qrcodePanel {
	width:220px;
	height:240px;
	text-align:center;
	background:#fff;
	border:solid 1px #ddd;
	position:absolute;
	left:0;
	top:0;
	overflow:hidden;
}
#floatPanel .popPanel .popPanel-inner .qrcodePanel img {
	width:200px;
	height:200px;
	border:none;
	padding:10px 10px 5px 10px;
}
#floatPanel .popPanel .popPanel-inner .qrcodePanel span {
	font-size:12px;
	color:#666;
	line-height:24px;
	letter-spacing:1px;
}
```
index code:
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>jQuery带微信的返回顶部/底部代码</title>
    <link href="css/style.css" rel="stylesheet" type="text/css" />
</head>
<body>
<div style="text-align:center;margin:5000px 0">
    <!--浮动面板-->
    <div id="floatPanel">
        <div class="ctrolPanel">
            <a class="arrow" href="#"><span>顶部</span></a>
            <a class="contact" href="www.baidu.com" target="_blank"><span>反馈</span></a>
            <a class="qrcode" href="#"><span>微信二维码</span></a>
            <a class="arrow" href="#"><span>底部</span></a>
        </div>
        <div class="popPanel">
            <div class="popPanel-inner">
                <div class="qrcodePanel">
                    <img src="images/myweichart.png" />
                    <span>扫描二维码关注我为好友</span>
                </div>
                <div class="arrowPanel">
                    <div class="arrow01">
                    </div>
                    <div class="arrow02">
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</body>
</html>
<script src="js/jquery-1.7.2.min.js"></script>
<script>
    $(function(){
        // 页面浮动面板
        $("#floatPanel > .ctrolPanel > a.arrow").eq(0).click(function(){$("html,body").animate({scrollTop :0}, 800);return false;});
        $("#floatPanel > .ctrolPanel > a.arrow").eq(1).click(function(){$("html,body").animate({scrollTop : $(document).height()}, 800);return false;});
        var objPopPanel = $("#floatPanel > .popPanel");
        var w = objPopPanel.outerWidth();
        $("#floatPanel > .ctrolPanel > a.qrcode").bind({
            mouseover : function(){
                objPopPanel.css("width","0px").show();
                objPopPanel.animate({"width" : w + "px"},300);return false;
            },
            mouseout : function(){
                objPopPanel.animate({"width" : "0px"},300);return false;
                objPopPanel.css("width",w + "px");
            }
        });
    });
</script>
```

