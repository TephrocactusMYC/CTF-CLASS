# level1
直接使用python内置的base64模块进行解码。
```python
import base64

# Base64-encoded string
base64_string = "cHduLmNvbGxlZ2V7Z0dBNWR1UjdUVnJmYno5d0lweThmS1VnS1FrLmROek56TURMMlFqTXlNeld9Cg=="

# Decode the string to bytes
base64_bytes = base64_string.encode('ascii')
message_bytes = base64.b64decode(base64_bytes)

# Decode the bytes to UTF-8 string
message = message_bytes.decode('utf-8')

print(message)

```
## ref
Base64编码和解码是一种将二进制数据转换为可打印ASCII字符格式的方法。该算法基于64个不同字符的子集，由大小写字母、数字、加号和正斜杠组成。

Base64编码的过程如下：

1. 将输入的二进制数据按每6个比特进行分组
2. 将每个6比特组转换为相应的Base64字符
3. 如果剩余比特数不足6比特，则使用等号（`=`）补齐。

例如，将ASCII字符`Man`进行Base64编码，可以按以下方式进行：

```
ASCII字符：     M       a       n
ASCII码（二进制） 01001101 01100001 01101110
6比特分组：     010011 010110 000101 101110
Base64字符：     S       m       F       u
```
因此，`Man`的Base64编码为`SmFu`。

Base64解码过程如下：

1. 将Base64编码的字符串转换为对应的二进制数据
2. 将二进制数据按每8个比特进行分组
3. 将每个8比特组转换为相应的ASCII字符

例如，将`SmFu`进行Base64解码，可以按以下方式进行：

```
Base64字符：     S       m       F       u
6比特分组：     010011 010110 000101 101110
ASCII码（二进制） 01001101 01100001 01101110
ASCII字符：     M       a       n
```

因此，`SmFu`的Base64解码为`Man`。

Base64编码和解码是一种常用的技术，用于在网络应用程序中传输二进制数据。通过编码二进制数据，可以确保它们传输时避免出现特殊字符或不受支持的格式。
# level2
```python
import base64

key_str = "xMQGl4LY1hyH7Khz155o3MedyLAedmm3H56HBvCvQHlzUkuTklt4ejKly8iRul/MH0kTNBGYpPGK3Q=="
ciphertext_str = "tLNoueG3unDii80I4/YptLXTj+NPJz7SZc7PWajGIREGIXvQ5ygwVFb3sYbr9xuALRh5eWjV3qb31w=="

# 解码密钥和密文
key = base64.b64decode(key_str)
ciphertext = base64.b64decode(ciphertext_str)

# 对密文使用密钥进行异或操作
plaintext = bytearray(len(ciphertext))
for i in range(len(ciphertext)):
    plaintext[i] = ciphertext[i] ^ key[i % len(key)]

# 将获得的字节序列转换为字符串
original_text = plaintext.decode('utf-8')

print(original_text)
```