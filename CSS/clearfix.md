# .clearfix

```css
.clearfix:after {
	visibility: hidden;
	display: block;
	content: "";
	clear: both;
	height: 0;
	}
* html .clearfix             { zoom: 1; } /* IE6 */
*:first-child+html .clearfix { zoom: 1; } /* IE7 */
```

