# yara
yara引擎，是一个规则匹配的工具。

好处在于其可以通过简单的编写规则来识别恶意代码，并且可以在各个平台下使用。
# yara规则
[官方文档](https://yara.readthedocs.io/en/stable/writingrules.html)

Each rule in YARA starts with the keyword rule followed by a rule identifier.

Rules are generally composed of two sections: strings definition and condition. The strings definition section can be omitted if the rule doesn't rely on any string, but the condition section is always required.

There are three types of strings in YARA: hexadecimal strings, text strings and regular expressions.

Starting with version 4.3.0, you may specify that a byte is not a specific value.

use jumps

regular expression