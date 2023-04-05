# Ldap

**Plugins to interact with the ldap server**

### Autor

[@akosej](https://github.com/akosej)

## Compilation

`> go build -buildmode=plugin -trimpath -o ldap.plugins ./main.go`

`> cp ldap.plugins pathAGA/plugins/`

### Functions exported

```go
Login(arg ...interface{}) interface{}

ListAll(secret ...interface{}) interface{}

Search(arg ...interface{}) interface{}

AddAccount(arg ...interface{}) interface{}

MoveAccount(arg ...interface{}) interface{}

DeleteAccount(arg ...interface{}) interface{}

ModifyAccount(arg ...interface{}) interface{}

ChangePasswordAccount(arg ...interface{}) interface{}
```

## How to use in AGA

1. Login.

```go
result := system.ExtractFunctionsPlugins("ldap", "Login", "user", "password")
fmt.Println(result.(bool))
```

2. ListAll -- List all ldap users

```go
result := system.ExtractFunctionsPlugins("ldap", "ListAll", nil)
bytes, _ := json.Marshal(&result)
var entries []ldap.Entry
_ = json.Unmarshal(bytes, &entries)
```

3. Search -- List all search users

```go
result := system.ExtractFunctionsPlugins("ldap", "Search", "(&(uid=user))")
bytes, _ := json.Marshal(&result)
var entries ldap.SearchResult
_ = json.Unmarshal(bytes, &entries)
```

4. AddUser -- Add user to ldap

```go
result := system.ExtractFunctionsPlugins("ldap", "AddAccount",
    "uid-->user",
    "ou-->(workers|students|visitors|corporatives|trash)",
    "dni-->dni",
    "uidNumber-->dni",
    "mail-->mail",
    "givenName-->first name",
    "sn-->surnames",
    "cn-->full name",
    "homeDirectory-->/home/aga",
    "description-->description",
    "businessCategory-->(user|admin)",
    "accountState-->(TRUE|FALSE)",
    "initials-->user_not_used",
    "userType-->(trabajador|estudiante|temporal|institucional)",
    ...
    )
fmt.Println(res) // Output: true | false
```
5. Move user in ldap
```go
result := system.ExtractFunctionsPlugins("ldap", "MoveAccount", "uid", (false|true), "(workers|students|visitors|corporatives|trash)")
fmt.Println(result) // Output: true | false
```
6. Delete user in ldap
```go
result := system.ExtractFunctionsPlugins("ldap", "DeleteAccount", "uid")
fmt.Println(result) // Output: true | false
```
7. Modify user in ldap
```go
result := system.ExtractFunctionsPlugins("ldap", "ModifyAccount", "uid", "Attribute-->value", ...)
fmt.Println(result) // Output: true | false
```
8. Modify password in ldap
`````go
result := system.ExtractFunctionsPlugins("ldap", "ChangePasswordAccount", "uid", "plain_text_password")
fmt.Println(result) // Output: true | false
```