 # 敏感字段加密规则

**    **<br>您只需花五分钟时间，详细阅读本文档，可以节省1~10小时的联调时间。<br>**
    
## 1.5.1综述

​		敏感字段统一使用联动公钥进行加密。

## 1.5.2 加密demo示例

```java
  public static String encode(String data) throws Exception {
	X509Certificate cert = returnX509Cer();
        byte[] keyBytes = cert.getPublicKey().getEncoded();
        // 取得公钥
        X509EncodedKeySpec x509KeySpec = new X509EncodedKeySpec(keyBytes);
        KeyFactory keyFactory = KeyFactory.getInstance("RSA");
        Key publicKey = keyFactory.generatePublic(x509KeySpec);

        Cipher cipher = Cipher.getInstance(keyFactory.getAlgorithm());
        cipher.init(Cipher.ENCRYPT_MODE, publicKey);
        String str = Base64.encode(cipher.doFinal(data.getBytes()));
        return str;
	}
  
  public static X509Certificate returnX509Cer() throws Exception {
	try {
            //转换成二进制流
            ByteArrayInputStream bais = new ByteArrayInputStream(getFileContent(keyFile));
            CertificateFactory cf = CertificateFactory.getInstance("X.509");
            X509Certificate xCert = (X509Certificate)cf.generateCertificate(bais);
            return xCert;
	} catch (Exception e) {
            throw new Exception("[UMF SDK] 秘钥内容读取错误", e);
	}
	}
  
  public static byte[] getFileContent(String fileName) throws Exception {
	byte[] data = (byte[]) null;
	FileInputStream fis = null;
	try {
            File f = new File(fileName);
            data = new byte[(int) f.length()];
            fis = new FileInputStream(f);
            fis.read(data);
	} catch (IOException e) {
            return null;
	} finally {
            if (fis != null) fis.close();
	}
	return data;
	}

```
**********demo结束，至此若均成功，说明成功**************
```

