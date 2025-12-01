---
title: Code examples
deprecated: false
hidden: true
metadata:
  robots: index
---
## Python example

```
import hashlib, hmac
def verify(appkey, token, timestamp, signature):
    return signature == hmac.new(
        key=appkey,
        msg='{}{}'.format(timestamp, token),
        digestmod=hashlib.sha256).hexdigest()
```

## Java examples

(Dependent <Anchor label="apache codec" target="_blank" href="https://commons.apache.org/proper/commons-codec/download_codec.cgi">apache codec</Anchor> )

```
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;

import org.apache.commons.codec.binary.Hex;

public boolean verify(String appkey, String token, long timestamp,
            String signature) throws NoSuchAlgorithmException, InvalidKeyException {
    Mac sha256HMAC = Mac.getInstance("HmacSHA256");
    SecretKeySpec secretKey = new SecretKeySpec(appkey.getBytes(),"HmacSHA256");
    sha256HMAC.init(secretKey);
    StringBuffer buf = new StringBuffer();
    buf.append(timestamp).append(token);
    String signatureCal = new String(Hex.encodeHex(sha256HMAC.doFinal(buf
            .toString().getBytes())));
    return signatureCal.equals(signature);
}
```

    
[WebHook analysis Sample download](https://www.aurorasendcloud.com/docs/downloads/java/CallBackController.zip)



PHP examples



```
function verify($appkey,$token,$timestamp,$signature){
    $hash="sha256";
    $result=hash_hmac($hash,$timestamp.$token,$appkey);
    return strcmp($result,$signature)==0?1:0;
}
```

**Experience Now**
If you don’t have url to receive data,try services of <Anchor label="requestb.in" target="_blank" href="http://requestb.in/">requestb.in</Anchor> or<Anchor label=" request 纷云版 " target="_blank" href="http://request.lesschat.com/"> request 纷云版 </Anchor> to experience WebHook.



1. Click **Create a RequestBin** to generate an **url   **
2. Configure the **URL** in SendCloud to receive event data from **WebHook**
3. After an operation (request, deliver, open), you can see all POST data of the event in **requestb.in**
