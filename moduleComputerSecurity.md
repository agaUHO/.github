# ComputerSecurity
> Module created for the areas of Customer Service, Information Security and network administrators

![logo](./seginfLogo.png)

## Searches and filters
   + `/computer-security/ldap/list-all`
     + Output is a json
       + UserStruct
   + `/computer-security/ldap/search/:filter`
     + The filter must be entered with the structure that LDAP requires, for example:
       + `&(attr=value)` _Specify the attributes according to the structure of your ldap_
       + `&(userType=Estudiante)(accountState=TRUE)` _Search for active students_
       + `&(ou:dn:=workers)` _Search by groups: workers | students | corporate | visitors_
       + `&(objectClass=person)(accountState=TRUE)(|(ou:dn:=workers)(ou:dn:=students))` _Example of an advanced search_
       
      - Output is a json:
         + UserStruct
         
      ### All outputs are structured in the following format, and we will refer to it as (UserStruct) throughout the documentation.
     ```json
     [
        {
          Id: int, // Consecutive number of the filter result
          AccountState: string, // TRUE or FALSE
          Dni: string,
          Uid: string,
          Cn: string,
          GivenName: string,
          Sn: string,
          Title: string,
          Initials: string, // user_not_used | update | expired_password | inactivity -- This attribute determines the descriptive status of the user
          Description: string,
          UserType: string, // Estudiante | Trabajador | Institucional | Temporal
          Roll: string,
          SecurityCode: string,     // TRUE or FALSE - If it is TRUE the twoFactor will be enabled
          MailEnabled: string,      // TRUE or FALSE
          ProxyEnabled: string,     // TRUE or FALSE
          RemoteEnabled: string,    // TRUE or FALSE
          ProxyAccess: string,      // TRUE or FALSE
          WifiEnabled: string,      // TRUE or FALSE
          NextcloudEnabled: string, // TRUE or FALSE
          MailAccessIn: string,
          Ma  ilAccessOut: string,
          MailQuota: string,
          ProxyQuota: string,
          RemotePhoneNumber: string,
          DeviceNumber: string,
          NextcloudQuota
          string
          Telegramuid: string,
          DhcpHWAddress: []
          string,
          //--Date ASSETS
          AssetsArea: string,
          AssetsDepartmentNumber: string,
          AssetsCategory: string,
          AssetsPosition: string,
          AssetsCategoryName: string,
          AssetsSubcategoryName: string,
          AssetsProfession: string,
          //--Date Sigenu
          Country: string,
          StudentType: string,
          Carrer: string,
          Faculty: string,
          CourseType: string,
          ScholasticOrigin: string,
          TownUniversity: string,
          MatriculationEndDate: string,
          ReMatriculationEndDate: string,
          StudentStatus: string,
          StudentYear: string,
          CreateUser: string,
          CreateDate: string,
          ModifyUser: string,
          ModifyData: string,
          UserPasswordSet: string,
          PassValid: string,
          PassSet: string,
          ExpireDate: string,
          HashModLdap: string,
          HashModApi: string,
          SyncRequired: bool,
          Ou: string
        },
        
      ]