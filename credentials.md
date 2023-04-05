
# AccessCredentialCard
**Plugins to generate the access credential card of the entry in jpg format**


## Autor
[@akosej](https://github.com/akosej)


## Compilation
`go build -buildmode=plugin -trimpath -o acc.plugins ./main.go`

## How to use the plugin
1. Create **credentials** folder in system **tools** folder, copy base fonts and images. 
2. Create **credentials** folder in system **static** folder, to save the generated image.
```
tools
    | credentials
        | font
            MuseoSans_500.ttf
            MuseoSans_700.ttf
        | img
            agaLogoBlue.png
            agaLogoGreen.png
            baseALCF.jpg //Base para acceso libre con foto
            baseALSF.jpg //Base para acceso libre sin foto
            baseAPCF.jpg //Base para acceso permamanete con foto
            baseAPSF.jpg //Base para acceso permamanete sin foto
            baseECF.jpg  //Base para acceso estudiantes con foto
            baseESF.jpg  //Base para acceso estudiantes sin foto
      
static
    | credentials
```

3. Create the structure to send the data in the function system.ExtractFunctionsPlugins

``` go
type accessCredentialCardDate struct {
	Uid      string
	TextQR   string
	Name     string
	Text     string
	UserType string
	Dni      string
	Access   string
}

/* 
ExtractFunctionsPlugins(plugins, function string, args ...interface{}) interface{}
_ = system.ExtractFunctionsPlugins(
		plugins:  "namePlugin",
		function: "nameFunction",
		args:     "style", accessCredentialCardDate{
			...
		})

Note: the style argument with the value (sf) to generate the overlap without personal photo, and value (cf) to generate it with personal photo.
*/
_ = system.ExtractFunctionsPlugins(
		"accessCredentials",
		"GetFunctions",
		"sf", # Opciones (sf) con foto, (cf) con foto
		accessCredentialCardDate {cf) 
			Uid:      "",
			TextQR:   "",
			Name:     "",
			Text:     "",
			UserType: "",
			Dni:      "",
			Access:   "",
		})

```

 