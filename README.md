#  新浪新闻
## 预览地址：
###  懒加载原理
```function isShow($node){
	var Scrolltop = $(window).scrollTop()
	var Height = $(window).height()
　　var elementH =　$node.offset().top

if(elementH < Scrolltop + Height){
	return true
}
else {
	return false
}
}
```
如果 滚动高度+可见高度 >= 内容高度，那么将更新页面。

### 瀑布流原理
```
function waterFallPlace($node){

var idx = 0,
minSumHeight = colSumHeight[0];

for(var i=0;i<colSumHeight.length; i++){
	if(colSumHeight[i] < minSumHeight){
		idx = i;
		minSumHeight = colSumHeight[i];
	}
}

$node.css({
	left: nodeWidth*idx,
	top: minSumHeight,
	opacity: 1
});

colSumHeight[idx] = $node.outerHeight(true) + colSumHeight[idx];
console.log(colSumHeight)
$('#pic-ct').height(Math.max.apply(null,colSumHeight));

}
```
加载图片时，对每列进行计算，如果某一列的高度最低，那么将该图片放在这一列，并且重新计算这一列的高度。

