<div align="center">

## Drag and Drop Layer<br/>by A Madarum


</div>

### Description

You can drag and drop layer as virtual window in your page
 
### More Info
 


<span>             |<span>
---                |---
**Category**       |Layers
**Level**          |Intermediate
**User Rating**    |3.9 (27 votes by 7 users)|
**Compatibility**  |





### Source Code

<HTML>
<HEAD><TITLE>Drag and Drop Layers</TITLE>
<SCRIPT LANGUAGE=JAVASCRIPT>
/*
* Name: Drag and Drop Layers
* Description:Drag and drop virtual window on your page
*
* note:
* i just test it in ie 5 and opera 6
* it can't work in netscape yet
* last modified 4/9/2002 12:57PM
*/
is_opera = (navigator.userAgent.toLowerCase().indexOf("opera") != -1);
var curObj = null; /* current object wich be drag */
var mouseY = 0;	/* mouse X */
var moousX = 0;	/* mouse Y */
var dx = 0;
var dy = 0;
function dragThis(what){
  var tmp;
  alert(what);
  if (document.all) tmp = document.all[what].style;
  else if (document.getElementById) tmp = document.getElementById(what).style;
  else if (document.layers) tmp=document.layers[what];
  curObj = tmp;
  var str = "";
  var i=0;
  str = tmp.left;	/* in ie style.left="12px" and in opere style.left="12" */
  i= (!is_opera) ? str.substr(0,str.length-2) : str;
  dx = mouseX - i;
  str = tmp.top;
  i= (!is_opera) ? str.substr(0,str.length-2) : str;
	dy = mouseY - i;
}
function mouseMove(e){
  mouseX = (document.all)? event.clientX : e.x;
  mouseY = (document.all)? event.clientY : e.y;
	if (curObj){
    curObj.left= mouseX - dx;
  	curObj.top = mouseY - dy;
	}
}
function mouseUp() {
	curObj = null;
}
if (document.layers)document.captureEvents(Event.MOUSEMOVE);
document.onmousemove=mouseMove;
document.onmouseup=mouseUp;
</SCRIPT>
</HEAD>
<BODY>
  <!------------- start layer ------------------>
  <script>
  	var tag="div";
  	if (document.layers) tag = "layer";
  	document.write("<"+tag+" id=\"winDrag\" style=\"position:absolute\">");
  </script>
  <TABLE><TR><TD bgcolor=000000>
  <TABLE bgcolor=ffffff><TR bgcolor=dcdcdc onmousedown="dragThis('winDrag')"><TD>X</TD></TR>
  <TR bgcolor=ffcccc><TD>
  <TABLE><TR><TD nowrap>Drag on the baner above<BR>by <CODE>xMadda</CODE></TD></TR></TABLE>
  </TD></TR></TABLE></TD></TR></TABLE>
  <script>
  	document.write("</"+tag+">");
  </script>
  <!------------- end layer -------------------->
</BODY>
</HTML>

