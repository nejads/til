# How to break long string in vim.

### Question:
Imagine to have a line as following
    String example = "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9Cg.MIIBYTCCAQcCAQAwbDEdMBsGA1UEAwwUSU1FSS0zNTg2NTAwODEwODM2NDQxCzAJBgNVBAYTAkRFMQ8wDQYDVQQIDAZCZXJsaW4xDzANBgNVBAcMBkJlcmxpbjEPMA0GA1UECgwGQ2FybWVxMQswCQYDVQQLDAJWVzBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABO28jh-lbpGBf_8TZ5OAx8GEYLY8yX7-9V4oU18m7xCqpvBpIpAytu_sCExD2UMIt2jaF3XRImCKymX2aaAgZcigOTA3BgkqhkiG9w0BCQ4xKjAoMA4GA1UdDwEB_wQEAwIHgDAWBgNVHSUBAf8EDDAKBggrBgEFBQcDAjAKBggqhkjOPQQDAgNIADBFAiBX6FcRCI3-YLa6-BAhGmd0Ehh6J4MvbgEtiiaBROulzgIhAIWEVU6R7aLP5zykMdxMqamVtQRdPdnCFjvvbqpoHj-C.NOTSIGNEdd";
How should we get a result as following:

```java
    String example = "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9Cg.MIIBYTCCAQcCAQAwb"
        + "DEdMBsGA1UEAwwUSU1FSS0zNTg2NTAwODEwODM2NDQxCzAJBgNVBAYTAkRFMQ8wDQYDVQQIDAZCZXJsa"
        + "W4xDzANBgNVBAcMBkJlcmxpbjEPMA0GA1UECgwGQ2FybWVxMQswCQYDVQQLDAJWVzBZMBMGByqGSM49A"
        + "gEGCCqGSM49AwEHA0IABO28jh-lbpGBf_8TZ5OAx8GEYLY8yX7-9V4oU18m7xCqpvBpIpAytu_sCExD2"
        + "UMIt2jaF3XRImCKymX2aaAgZcigOTA3BgkqhkiG9w0BCQ4xKjAoMA4GA1UdDwEB_wQEAwIHgDAWBgNVH"
        + "SUBAf8EDDAKBggrBgEFBQcDAjAKBggqhkjOPQQDAgNIADBFAiBX6FcRCI3-YLa6-BAhGmd0Ehh6J4Mvb"
        + "gEtiiaBROulzgIhAIWEVU6R7aLP5zykMdxMqamVtQRdPdnCFjvvbqpoHj-C.NOTSIGNEdd";
```

### Answer

First you need to break line on for example 80 by following command

1. Select the line by Visual mode 

2. :s/\v(.{80})/\1\r/g

   This will add a newline at the end of every 80th character.

   ```
   :s/       replaces within the current select
   \v        uses regular expressions
   (.{80})   selects 80 characters & placed them into group one
   \1\r      replaces group one with group one and a newline
   ```

You get something as follwoing 

```java
    String example = "eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzI1NiJ9Cg.MIIBYTCCAQcCAQAwb
DEdMBsGA1UEAwwUSU1FSS0zNTg2NTAwODEwODM2NDQxCzAJBgNVBAYTAkRFMQ8wDQYDVQQIDAZCZXJsa
W4xDzANBgNVBAcMBkJlcmxpbjEPMA0GA1UECgwGQ2FybWVxMQswCQYDVQQLDAJWVzBZMBMGByqGSM49A
gEGCCqGSM49AwEHA0IABO28jh-lbpGBf_8TZ5OAx8GEYLY8yX7-9V4oU18m7xCqpvBpIpAytu_sCExD2
UMIt2jaF3XRImCKymX2aaAgZcigOTA3BgkqhkiG9w0BCQ4xKjAoMA4GA1UdDwEB_wQEAwIHgDAWBgNVH
SUBAf8EDDAKBggrBgEFBQcDAjAKBggqhkjOPQQDAgNIADBFAiBX6FcRCI3-YLa6-BAhGmd0Ehh6J4Mvb
gEtiiaBROulzgIhAIWEVU6R7aLP5zykMdxMqamVtQRdPdnCFjvvbqpoHj-C.NOTSIGNEdd";
```

Second you need to add + " to the beginning of the line and " to the end of lines. You can do it manually or preferably editing in multiple lines by following commands [[ref]](https://stackoverflow.com/a/9549765)

1. Move the cursor to the beginning of the first line that you want edit. In this case DEdMB...
2. Enter visual block mode Ctrl+v.
3. Select the lines that you want edit at the same time. 
4. Press `I` (capital i).
5. Add + " to the beginning and " to the end of first line (Note: It will only update the screen in the first line - until Esc is pressed)
6. Press Esc 



