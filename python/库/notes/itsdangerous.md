[TOC]

# itsdangerous
官方文档：https://itsdangerous.palletsprojects.com/en/latest/

## 安装

> `pip install itsdangerous`

## 使用

#### 在 `Django` 中加密解密的使用（JSON Web Signature——JWS）

文档：https://itsdangerous.palletsprojects.com/en/1.1.x/jws/

参考：https://www.codenong.com/cs106291242/

`itsdangerous` 已在新版本中删除对 `JWS` 的支持

1. 有过期时间的签名——TimedJSONWebSignatureSerializer

    未过期时可以解密
    ```py
    from itsdangerous import TimedJSONWebSignatureSerializer # 导入时间JSON签名序列化包
    In[2]:serializer1 = TimedJSONWebSignatureSerializer(secret_key='secret-key', expires_in=3600)    # 密钥和过期时间
    In[3]:info = {'content':9527}   # JSON，也可以是list类型、字符串类型
    In[4]:res = serializer1.dumps(info) # 加密
    In[5]:res
    Out[5]: b'eyJhbGciOiJIUzUxMiIsImlhdCI6MTU5MDE1MDQ0MywiZXhwIjoxNTkwMTU0MDQzfQ.eyJjb250ZW50Ijo5NTI3fQ.SyIcvnG8yOHPA1teNhK3htc50WgWHJxA9-4-6DS0Zlk4Q4zWV5GKUAv2axmhio4ry0YdQls5Lc1eoIZDR8Cvdw'
    In[6]:serializer1.loads(res)    # 解密
    Out[6]: {'content': 9527}
    ```

    过期后解密会报错
    ```py
    In[7]:serializer1 = TimedJSONWebSignatureSerializer(secret_key='secret-key', expires_in=1) # 1秒后过期
    In[8]:res = serializer1.dumps(info)
    In[9]:serializer1.loads(res)
    Traceback (most recent call last):
    File "D:\Python3.7.5\lib\site-packages\IPython\core\interactiveshell.py", line 3319, in run_code
        exec(code_obj, self.user_global_ns, self.user_ns)
    File "<ipython-input-26-9a4867386e07>", line 1, in <module>
        serializer1.loads(res)
    File "D:\Python3.7.5\lib\site-packages\itsdangerous\jws.py", line 205, in loads
        date_signed=self.get_issue_date(header),
    itsdangerous.exc.SignatureExpired: Signature expired`
    ```