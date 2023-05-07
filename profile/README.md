# AGA
### Adaptar - Gestionar - Automatizar

## Plugins
[TowFactor](./2fa.md) Autor:@akosej

## Modules
[ModuleComputerSecurity](./moduleComputerSecurity.md)


## System routes

+ `/aga/`
    + Output is a html
        + Returns the system documentation
+ `/aga/login`
    + This url is to login to the system, you must send BODY in raw format with application/json by POST method:

        + `{"username": "$val1", "password": "$val2", "securitycode": "$val3"}`
            + `$val1` _Specify the user_
            + `$val2` _Type the password in plain text_
            + `$val3` _Specify the 6-digit 2fa code_
    + Output is a json:

      + ```json
            {
        "OK": true,
        "activeUser": {
            "status": 200,
            "account_state": "TRUE",
            "uid": "pepepp",
            "personal_information": {
              "dni": "87042543541",
              "cn": "Pepe Perez Perez",
              "given_name": "Pepe",
              "sn": "Perez Perez"
            },
            "account_info": {
              "user_type": "Institucional",
              "expire_date": "",
              "description": "",
              "title": "",
              "initials": "update",
              "create_user": "[ej]",
              "create_date": "2022-10-22 02:02:12 am",
              "modify_user": "akos",
              "modify_data": "2022-10-22 03:35:08 am",
              "password": {
              "user_password_set": "2022-10-22 03:35:08 am",
              "pass_valid": "Expirado",
              "pass_set": "191"
            },
            "synchro": {
              "hash_mod_ldap": "",
              "hash_mod_api": "",
              "sync_required": false
            },
            "ou": "corporatives"
            },
            "permissions": [],
            "other_accounts": null,
            "preference": {
              "color": "",
              "theme_dark": "",
              "orc_id": "",
              "facebook": "",
              "twitter": "",
              "instagram": "",
              "telegram": "",
              "whats_app": "",
              "research_gate": "",
              "linked_in": "",
              "google": ""
            },
            "service": {
              "mail": {
                "enabled": "TRUE",
                "access_in": "internac-in",
                "access_out": "internac-out",
                "quota": "1048576"
              },
              "proxy": {
                "enabled": "TRUE",
                "access": "internac",
                "quota": "0"
              },
              "nextcloud": {
                "enabled": "FALSE",
                "quota": "0"
              },
              "Remote": {
                "enabled": "FALSE",
                "phone_number": ""
              },
              "wifi": {
                "enabled": "TRUE",
                "device_number": "1",
                "macaddress": []
              }
            },
            "assets": {
              "area": "",
              "department_number": "",
              "category": "",
              "position": "",
              "category_name": "",
              "subcategory_name": "",
              "profession": ""
            },
            "sigenu": {
              "country": "",
              "student_type": "",
              "carrer": "",
              "faculty": "",
              "course_type": "",
              "scholastic_origin": "",
              "town_university": "",
              "matriculation_end_date": "",
              "re_matriculation_end_date": "",
              "student_status": "",
              "student_year": ""
            },
            "two_factor": {
              "status": "false",
              "qr": ""
            }
        },
        "message": "success"
        }
        ```
    + Status

        + ``200`` _success_
        + ``401`` _Credenciales incorrectas | 2fa incorrect_
        + ``409`` _Format error in user or password_
        + ``500`` _could not login_
+ `/aga/logout`
  + This url is to log out of the system, POST method
  + Output

    +
      ```json
        {
          "message": "success|false",
        }
        ```

  + Status
    + `200` _Success_
    + `401` _Error_
+ `/aga/active`
  + Returns the data of the logged in user with the structure of (activeUser)
