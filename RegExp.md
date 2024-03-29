## 常用正则公式

#### 校验数字的表达式

|title|rule(会有多个正则)|memo|
|:--|:--|:--|
|数字|`^[0-9]*$`|
|n位的数字|`^\d{n}$`|
|至少n位的数字|`^\d{n,}$`|
|m-n位的数字|`^\d{m,n}$`|
|零和非零开头的数字|`^(0|[1-9][0-9]*)$`|
|非零开头的最多带两位小数的数字|`^([1-9][0-9]*)+(.[0-9]{1,2})?$`|
|带1-2位小数的正数或负数|`^(\-)?\d+(\.\d{1,2})?$`|
|正数、负数、和小数|`^(\-|\+)?\d+(\.\d+)?$`|
|有两位小数的正实数|`^[0-9]+(.[0-9]{2})?$`|
|有1~3位小数的正实数|`^[0-9]+(.[0-9]{1,3})?$`|
|非零的正整数|`^[1-9]\d*$`<br/>`^([1-9][0-9]*){1,3}$`<br/>`^\+?[1-9][0-9]*$`|
|非零的负整数|`^\-[1-9][]0-9"*$`<br/>`^-[1-9]\d*$`|
|非负整数|`^\d+$`<br/>`^[1-9]\d*|0$`|
|非正整数|`^-[1-9]\d*|0$`<br/>`^((-\d+)|(0+))$`|
|非负浮点数|`^\d+(\.\d+)?$`<br/>`^[1-9]\d*\.\d*|0\.\d*[1-9]\d*|0?\.0+|0$`|
|非正浮点数|`^((-\d+(\.\d+)?)|(0+(\.0+)?))$`<br/>`^(-([1-9]\d*\.\d*|0\.\d*[1-9]\d*))|0?\.0+|0$`|
|正浮点数|`^[1-9]\d*\.\d*|0\.\d*[1-9]\d*$`<br/>`^(([0-9]+\.[0-9]*[1-9][0-9]*)|([0-9]*[1-9][0-9]*\.[0-9]+)|([0-9]*[1-9][0-9]*))$`|
|负浮点数|`^-([1-9]\d*\.\d*|0\.\d*[1-9]\d*)$`<br/>`^(-(([0-9]+\.[0-9]*[1-9][0-9]*)|([0-9]*[1-9][0-9]*\.[0-9]+)|([0-9]*[1-9][0-9]*)))$`|
|浮点数|`^(-?\d+)(\.\d+)?$`<br/>`^-?([1-9]\d*\.\d*|0\.\d*[1-9]\d*|0?\.0+|0)$`|
|数字以英文逗号隔开|`^\d+(,\d+)*$`|`/^\d+(,\d+)*$/.test('1,2,3,4,5')`|

#### 校验字符的表达式

|title|rule(会有多个正则)|memo|
|:--|:--|:--|
|汉字|`^[\u4e00-\u9fa5]{0,}$`|
|英文和数字|`^[A-Za-z0-9]+$`<br/>`^[A-Za-z0-9]{4,40}$`|
|长度为3-20的所有字符|`^.{3,20}$`|
|由26个英文字母组成的字符串|`^[A-Za-z]+$`|
|由26个大写英文字母组成的字符串|`^[A-Z]+$`|
|由26个小写英文字母组成的字符串|`^[a-z]+$`|
|由数字和26个英文字母组成的字符串|`^[A-Za-z0-9]+$`|
|由数字、26个英文字母或者下划线组成的字符串|`^\w+$`<br/>`^\w{3,20}$`|
|中文、英文、数字包括下划线|`^[\u4E00-\u9FA5A-Za-z0-9_]+$`|
|中文、英文、数字但不包括下划线等符号|`^[\u4E00-\u9FA5A-Za-z0-9]+$`<br/>`^[\u4E00-\u9FA5A-Za-z0-9]{2,20}$`|
|可以输入含有^%&',;=?$\"等字符|`[^%&',;=?$\x22]+`|
|禁止输入含有 ~ 的字符|`[^~\x22]+`|
    
#### 特殊需求表达式

|title|rule(会有多个正则)|memo|
|:--|:--|:--|
|Email地址|`^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$`||
|域名|`[a-zA-Z0-9][-a-zA-Z0-9]{0,62}(/.[a-zA-Z0-9][-a-zA-Z0-9]{0,62})+/.?`||
|InternetURL|`[a-zA-z]+://[^\s]*`<br/>`^http://([\w-]+\.)+[\w-]+(/[\w-./?%&=]*)?$`||
|手机号码|`^1[3456789]\d{9}$`||
|电话号码|`^(\(\d{3,4}-)|\d{3.4}-)?\d{7,8}$`|XXX-XXXXXXX、XXXX-XXXXXXXX、XXX-XXXXXXX、XXX-XXXXXXXX、XXXXXXX 和 XXXXXXXX|
|国内电话号码|`\d{3}-\d{8}|\d{4}-\d{7}`|0511-4405222、021-87888822|
|身份证号|`^\d{15}|\d{18}$`|15位、18位数字|
|短身份证号码|`^([0-9]){7,18}(x|X)?$`<br/>`^\d{8,18}|[0-9x]{8,18}|[0-9X]{8,18}?$`|数字、字母x结尾|
|帐号是否合法|`^[a-zA-Z][a-zA-Z0-9_]{4,15}$`|字母开头，允许5-16字节，允许字母数字下划线|
|密码|`^[a-zA-Z]\w{5,17}$`|以字母开头，长度在6~18之间，只能包含字母、数字和下划线|
|强密码|`^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,10}$`|必须包含大小写字母和数字的组合，不能使用特殊字符，长度在8-10之间|
|日期格式|`^\d{4}-\d{1,2}-\d{1,2}`|
|一年的12个月|`^(0?[1-9]|1[0-2])$`|01～09和1～12|
|一个月的31天|`^((0?[1-9])|((1|2)[0-9])|30|31)$`|01～09和1～31|
|一个0或者一个不以0开头的数字.我们还可以允许开头有一个负号|`^(0|-?[1-9][0-9]*)$`||
|xml文件|`^([a-zA-Z]+-?)+[a-zA-Z0-9]+\\.[x|X][m|M][l|L]$`||
|中文字符的正则表达式|`[\u4e00-\u9fa5]`||
|双字节字符|`[^\x00-\xff]`|包括汉字在内，可以用来计算字符串的长度(一个双字节字符长度计2，ASCII字符计1)|
|空白行的正则表达式|`\n\s*\r`|可以用来删除空白行|
|HTML标记的正则表达式|`<(\S*?)[^>]*>.*?</\1>|<.*? />`||
|首尾空白字符的正则表达式|`^\s*|\s*$或(^\s*)|(\s*$)`||
|腾讯QQ号|`[1-9][0-9]{4,}`||
|中国邮政编码|`[1-9]\d{5}(?!\d)`|中国邮政编码为6位数字|
|IP地址|`\d+\.\d+\.\d+\.\d+`|提取IP地址时有用|
|emoji|`/\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDE4F]/g`||
