# 2FA

**2fa**

### Autor

[@akosej](https://github.com/akosej)

## How to use

1. Get 2fa Code.

```go
result := system.ExtractFunctionsPlugins(
"2fa",
"F2a",
"user@domain")

fmt.Println(result)
```

2. GetQr -- Extract QR img base64 

```go
result := system.ExtractFunctionsPlugins(
"2fa",
"GetQr",
"user@domain")

fmt.Println(result)
```

## How to use route
1. Open webBrowser
2. Access in http://url_system/aga/2fa/:uid/:code

### Where:
1. **url_system** = Url system hosted
2. **:uid** = username
3. **:code** = code_6_number

### Output code
1. **409** Conflict 
2. **406** NotAcceptable 
3. **403** Forbidden 
4. **200** Ok 
