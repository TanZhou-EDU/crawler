#字符串常用函数
| 函数 | 作用 |返回值| 示例  |
| :--------| :-----:|:----: |:----: |
|   len     |获取字符串长度|Number| len(str)|
| upper     |转为大写  |String |  str.upper() |
| lower     |转为小写  |String| str.lower()  |
|swapcase   |大小写互转|String|str.swapcase()|
|title      |每个单词首字母大写|String|str.title()|
|capitalize |首字母大写|String|str.capitalize()|
|ljust(width[,'填充字符'])      |把字符串填充为指定长度,<br>左对齐填充<br>右边不够默认用空格补齐|Number|str.ljust(30)|
|rjust(width[,'填充字符'])      |把字符串填充为指定长度,<br>右对齐填充<br>左边不够默认用空格补齐|Number|str.rjust(30)|
|center(width[,'填充字符'])     |把字符串填充为指定长度,<br>中间对齐填充<br>中间不够默认用空格补齐|Number|str.center(30)|
|zfill      |用0填充固定长度字符串|String|str.zfill(30)|
|find(sub[,start[,end]])|在字符串中搜索子字符串是否存在|-1  不存在<br>num 搜索到的字符串起始位置|str.find('is', 8, len(str))|
|rfind|从字符串末尾开始搜索子字符串是否存在|-1 不存在<br>从右搜索到的字符串位置|str.rfind('s')|
|index(sub[,start[,end]])|在字符串中搜索子字符串是否存在|找不到会抛出异常|str.index('s', 0,len(str))|
|count(sub[,start])|统计字符串出现次数<br>start 查找开始位置|返回找到的个数|str.count('s')|
|replace(old, new[,count])|在字符串中替换,count替换次数|替换后的String|str.replace('py,'aa')|
|strip([chars])|去除左右两边指定字符,默认去除空格|String|str.strip()|
|lstrip([chars])|去除左边指定字符,默认去除空格|String|str.lstrip()|
|rstrip([chars])|去除右边指定字符,默认去除空格|String|str.rstrip()|
|startswith|判断是否以指定字符开头|Bool|str.startswith('s')|
|endswith|判断是否以指定字符结尾|Bool|str.endswith('end')|
|isalnum|是否都是由字母或数字组成|Bool|str.isalnum()|
|isalpha|是否全为字母,汉字作为字母处理|Bool|str.isalpha()|
|isdigit,isnumeric, isdecimal|是否全为数字|Bool|str.isdigit()|
|isspace|是否全为空白符|Bool|str.isspace()|
|isupper|是否全是大写|Bool|str.isupper()|
|islower|是否全是小写|Bool|str.islower()|
|istitle|每个字母是否都是大写|Bool|str.istitle()|
|split  |使用指定字符拆分字符串|list列表|str.split(',')|
|join({},(),[])   |使用指定字符合并连接一个list序列<br>list的每个元素必须是字符串|合并后的字符串|'-'.join(['aa','bb','cc'])|
|encode|编码函数|class bytes|str.encode('utf-8')|
|decode|解码函数|class bytes|str.decode('utf-8')|




