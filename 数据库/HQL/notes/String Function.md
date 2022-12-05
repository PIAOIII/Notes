[TOC]

# String Function

## translate()
| 返回值 | name(signature)   | 说明 |
| ------ | ----------------- | ---- |
| String | `translate(string|char|varchar input, string|char|varchar from, string|char|varchar to)` | 如下 |

说明：
**逐个检查**input字符串**每个字符**，如果在input中的某个字符在from的字符串中存在，则替换为在to字符串中的**相同位置**下的字符。
如果to字符串比from短，那么在from字符串中的某个字符可能在to字符串中**找不到**相应的字符，那么就会在原字符串input中**删除**这个字符

示例：
对于字符串："2022-12-01 12:34:56"，去除所有非数字字符
> select translate("2022-12-01 12:34:56", " -:", "")
> -> 20221201123456 