# Naming standards

## Introduction
The first pillar of the scaffold is naming standards. Well-designed naming standards enable to identify resources in the portal, on a bill, and within scripts. Most likely, there are already naming standards for on-premises infrastructure. When adding Azure to your environment, those naming standards should be extended to your Azure resources. Naming standard facilitate more efficient management of the environment at all levels.

The choice of a name for any resource in Microsoft Azure is important because:

  - It is difficult to change a name later.

  - Names must meet the requirements of their specific resource type.

Consistent naming conventions make resources easier to locate. They can also indicate the role of a resource in a solution.

The key to success with naming conventions is establishing and following them across your applications and organizations.

## Technical Background
Sources: <https://docs.microsoft.com/en-us/azure/architecture/best-practices/naming-conventions>, <https://blogs.technet.microsoft.com/dsilva/2017/11/10/azure-subscription-governance-resource-group-and-naming-convention-strategies/>

### Subscriptions

When naming Azure subscriptions, verbose names make understanding the context and purpose of each subscription clear. When working in an environment with many subscriptions, following a shared naming convention can improve clarity.

A generic recommended pattern for naming subscriptions is:

**\<Company\> \<Department (optional)\> \<Product Line (optional)\> \<Environment\>**

  - Company would usually be the same for each subscription. However, some companies may have child companies within the organizational structure. These companies may be managed by a central IT group. In these cases, they could be differentiated by having both the parent company name and child company name.

  - Department is a name within the organization that contains a group of individuals. This item within the namespace is optional. For example: “IT”, “Marketing”, …

  - Product line is a specific name for a product or function that is performed from within the department. This is generally optional for internal-facing services and applications. However, it is highly recommended to use for public-facing services that require easy separation and identification (such as for clear separation of billing records).

  - Environment is the name that describes the deployment lifecycle of the applications or services, such as Dev, Test, or Prod.

### Rules and restrictions

Each resource or service type in Azure enforces a set of naming restrictions and scope; any naming convention or pattern must adhere to the requisite naming rules and scope. For example, while the name of a VM maps to a DNS name (and is thus required to be unique across all of Azure), the name of a VNET is scoped to the Resource Group that it is created within.

In general, avoid having any special characters (- or \_) as the first or last character in any name. These characters will cause most validation rules to fail.

#### General naming restrictions

| Entity           | Scope             | Length                  | Case sensitive | Valid Characters                                                          | Suggested Pattern                         | Example                     |
| ---------------- | ----------------- | ----------------------- | -------------- | ------------------------------------------------------------------------- | ----------------------------------------- | --------------------------- |
| Resource Group   | Subscription      | 1-90                    | false          | Alphanumeric, underscore, parentheses, hyphen, and period (except at end) | \<service short name\>-\<environment\>-rg | profx-prod-rg               |
| Availability Set | Resource Group    | 1-80                    | false          | Alphanumeric, underscore, and hyphen                                      | \<service-short-name\>-\<context\>-as     | profx-sql-as                |
| Tag              | Associated Entity | 512 (name), 256 (value) | false          | Alphanumeric                                                              | "key" : "value"                           | "department" : "Central IT" |

#### Compute naming restrictions

| Entity          | Scope          | Length                           | Case sensitive | Valid Characters        | Suggested Pattern              | Example         |
| --------------- | -------------- | -------------------------------- | -------------- | ----------------------- | ------------------------------ | --------------- |
| Virtual Machine | Resource Group | **1-15 (Windows), 1-64 (Linux)** | false          | Alphanumeric and hyphen | \<name\>-\<role\>-vm\<number\> | profx-sql-vm1   |
| Function App    | Global         | 1-60                             | false          | Alphanumeric and hyphen | \<name\>-func                  | calcprofit-func |

For all rules and restrictions, please visit [https://docs.microsoft.com/en-us/azure/architecture/best-practices/naming-conventions\#naming-rules-and-restrictions](https://docs.microsoft.com/en-us/azure/architecture/best-practices/naming-conventions).

### Affixes

When developing a  naming convention for a company or project, it is important to select a common set of affixes and their position (suffix or prefix).

While all the information about type, metadata and context is available via API, applying common affixes simplifies visual identification. When incorporating affixes into your naming convention, it is important to clearly specify whether the affix is at the beginning of the name (prefix) or at the end (suffix).

For instance, here are two possible names for a service hosting a calculation engine:

  - SvcCalculationEngine (prefix)

  - CalculationEngineSvc (suffix)

Affixes can refer to different aspects that describe the particular resources. See in the examples under chapter application.

[recommendations]: # ( start )
## Good Practices: Naming standards
### Affixes
#### Region
| Region               | Location             | Code     |
| -------------------- | -------------------- | -------- |
| Region Neutral       | Location Neutral     | **AAAA** |
| South Africa North   | Johannesburg         | SANO     |
| South Africa West    | Cape Town            | SAWE     |
| Central India        | Pune                 | INCE     |
| China East           | Shanghai             | CHEA     |
| China East 2         | Shanghai             | CHE2     |
| China North          | Beijing              | CHNO     |
| China North 2        | Beijing              | CHN2     |
| East Asia            | Hong Kong            | ASEA     |
| Japan East           | Tokyo, Saitama       | JAEA     |
| Japan West           | Osaka                | JAWE     |
| Korea Central        | Seoul                | KOCE     |
| Korea South          | Busan                | KOSO     |
| South India          | Chennai              | INSO     |
| Southeast Asia       | Singapore            | ASSO     |
| UAE Central          | Abu Dhabi            | UACE     |
| UAE North            | Dubai                | UANO     |
| West India           | Mumbai               | INWE     |
| Australia Central    | Canberra             | AUCE     |
| Australia Central 2  | Canberra             | AUC2     |
| Australia East       | New South Wales      | AUEA     |
| Australia Southeast  | Victoria             | AUSO     |
| France Central       | Paris                | FRCE     |
| France South         | Marseille            | FRSO     |
| Germany Central      | Frankfurt            | GECE     |
| Germany North        | Germany North        | GENO     |
| Germany Northeast    | Magdeburg            | GENE     |
| Germany West Central | Germany West Central | GEWC     |
| North Europe         | Ireland              | EUNO     |
| Norway East          | Norway               | NOEA     |
| Norway West          | Norway               | NOWE     |
| Switzerland North    | Zurich               | SCNO     |
| Switzerland West     | Geneva               | SCWE     |
| UK South             | London               | UKSO     |
| UK West              | Cardiff              | UKWE     |
| West Europe          | Netherlands          | **EUWE** |
| Canada Central       | Toronto              | CACE     |
| Canada East          | Quebec City          | CAEA     |
| Central US           | Iowa                 | USCE     |
| East US              | Virginia             | USEA     |
| East US 2            | Virginia             | USE2     |
| North Central US     | Illinois             | USNC     |
| South Central US     | Texas                | USSC     |
| US DoD Central       | Iowa                 | USGC     |
| US DoD East          | Virginia             | USGE     |
| US Gov Arizona       | Arizona              | USGA     |
| US Gov Iowa          | Iowa                 | USGI     |
| US Gov Texas         | Texas                | USGT     |
| US Gov Virginia      | Virginia             | USGV     |
| West Central US      | Wyoming              | UWCE     |
| West US              | California           | USW2     |
| West US 2            | Washington           | USWE     |
| Brazil South         | Sao Paulo State      | BRSO     |
| Azure Stack          | Datacenter           | AZBE     |

#### Environment
| Code | Description   |
| ---- | ------------- |
| DE   | Development   |
| TE   | Test          |
| ST   | Staging (UAT) |
| PR   | Production    |
| CO   | Core          |
| AU   | Automation    |
| SB   | Sandbox       |
| SP   | Special       |
| UN   | Undefined     |

#### Services
| Name                                          | Category     | Prefix | Suffix |
| --------------------------------------------- | ------------ | ------ | ------ |
| App Service                                   | App Services | aps    |        |
| App Service                                   | App Services | aps    |        |
| App Service Environment                       | App Services | ase    |        |
| App Service Plan                              | App Services | asp    |        |
| Application Insights                          | App Services | AIS    |        |
| Application Security Group                    |              | ASG    |        |
| Automation Account                            | Serverless   | AUT    |        |
| Availability Set                              | Compute      | AVS    |        |
| Azure Analysis Services                       | Databases    | aas    |        |
| Azure Application Gateway                     | Security     | AAG    |        |
| Azure Automation Hybrid Worker                | Hybrid       |        |        |
| Azure Traffic Manager Profile                 | Networking   | ATM    |        |
| Blob                                          | Storage      |        |        |
| Blueprints                                    | Governance   | BLP    |        |
| Container                                     | Serverless   |        |        |
| Data Lake Store                               | Storage      |        |        |
| Event Grid Domains	Event Hub                  | Serverless   | egd    |        |
| Event Grid Subscriptions	Event Hub            | Serverless   | egs    |        |
| Event Hubs	Event Hub                          | Serverless   | evh    |        |
| Event Hubs Topics	Event Hub                   | Serverless   | egt    |        |
| External Load Balancer                        | Compute      | LBE    |        |
| File                                          | Storage      |        |        |
| Function                                      | Serverless   |        |        |
| Initative                                     | Governance   |        |        |
| Internal Load Balancer                        | Networking   | LBI    |        |
| Key Vault                                     | Other        | key    |        |
| Load Balancer	Networking                      | Networking   | llb    |        |
| Load Balancing Rules Config                   | Networking   | LBR    |        |
| Log Analytics Workspace                       | Monitoring   | LAW    |        |
| Log Analytics Workspace	Other                 | Monitoring   | law    |        |
| Managed Disk	Storage                          | Storage      |        |        |
| Management Group                              | Governance   | MAG    |        |
| Network Interface                             | Networking   | NIC    |        |
| Network Security Group                        | Networking   | NSG    |        |
| Network Security Group Rule                   | Networking   |        |        |
| Policies                                      | Governance   |        |        |
| Public IP Address                             | Networking   | PIP    |        |
| Public IP Address	Networking                  | Networking   | pub    |        |
| Queue                                         | Serverless   |        |        |
| Recovery Service Vault	Storage                | Backup       | rsv    |        |
| Recovery Services Vault                       | Backup       | RSV    |        |
| Recovery Services Vault – Azure Backup Policy | Backup       | ABP    |        |
| Ressource Group                               | Governance   | RSG    |        |
| Route Table                                   | Networking   | NRT    |        |
| SQL Database	Databases                        | Database     | sdb    |        |
| SQL Datawarehouse	Databases                   | Database     | sdb    |        |
| SQL Managed Instance	Databases                | Database     | smi    |        |
| SQL Server	Databases                          | Database     | sdb    |        |
| Storage Account                               | Storage      |        |        |
| Storage Account Name (data)                   | Storage      |        |        |
| Storage Account Name (disk)                   | Storage      |        |        |
| Subnet                                        | Networking   | SNE    |        |
| Subscription                                  | Governance   | SUB    |        |
| Table                                         | Databases    |        |        |
| Tag                                           | Governance   |        |        |
| Virtual Machine                               | Compute      |        |        |
| Virtual Network (VNet)                        | Networking   | VNE    |        |
| VNet Peering                                  | Networking   | VNP    |        |
| VPN Gateway                                   | Networking   | VPN    |        |

### Naming Conventions

If this naming convention used only for a single-tenant, you can omit the **TenantShort** term. But if you are an MSP/CSP or uses services from it, it recommended that you use this in your notation.

#### Management Group

*Corp Pattern*: `<Prefix>_<CORP|TenantShort>_<Level>` \
*Corp ID Pattern*: `<Prefix>_<ManagementGroupID>_<Level>`

*Name Pattern*: `<Prefix>_[TenantShort]_<Scope>_<Level>` \
*ID Pattern*: `<Prefix>_<ManagementGroupID>_<Level>`

*Examples*:

| ID          | Name            |
| ----------- | --------------- |
| MAG_0001_00 | MAG_CORP_00     |
| MAG_0002_01 | MAG_Infra_01    |
| MAG_0003_01 | MAG_Standard_01 |
| MAG_0004_01 | MAG_Special_01  |
| MAG_0005_02 | MAG_SuplierA_02 |
| MAG_0006_02 | MAG_SuplierB_02 |

| ID          | Name                 |
| ----------- | -------------------- |
| MAG_0007_00 | MAG_MYTC_00          |
| MAG_0008_01 | MAG_MYTC_Infra_01    |
| MAG_0009_01 | MAG_MYTC_Standard_01 |

*Description*:

| Identifiers       | Range | Values/Meaning                                                                | Comments |
| ----------------- | ----- | ----------------------------------------------------------------------------- | -------- |
| Prefix            | 3     | MAG = Management Group                                                        |          |
| ManagementGroupID | 4     | Ongoing numbering                                                             |          |
| TenantShort       | 4     | MYTC = My Top Company                                                         |          |
| Scope             | 5..30 | Infra <br> Standard <br> Special <br> Others                                  |          |
| Level             | 2     | 00 = Top Level <br> 01 = Level under Top Level <br> 02 = Level under Level 01 |          |


#### Subscription
*Pattern*:
`<Prefix>_[TenantShort]_<Environment>_<SubscriptionID>_<Product|Service|Team>_<VersionNr>`

*Examples*:

SUB_AU_0001_CentralAutomation_01\
SUB_CO_0001_CentralServices_01\
SUB_SB_0001_CentralSandbox_01\
SUB_PR_1001_BusinesServices_01

SUB_MYTC_AU_0001_CentralAutomation_01\
SUB_MYTC_CO_0001_CentralServices_01\
SUB_MYTC_SB_0001_CentralSandbox_01\
SUB_MYTC_PR_1001_BusinesServices_01\
SUB_MYTC_TE_1002_BusinesServices_01\
SUB_MYTC_DE_1003_BusinesServices_01\
SUB_MYTC_PR_1004_VDIServices_01\
SUB_MYTC_SP_2001_ExternalCorpA_01

*Description*:

| Identifiers            | Range | Values/Meaning                                                                                                                              | Comments |
| ---------------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Prefix                 | 3     | SUB = Subscription                                                                                                                          |          |
| TenantShort            | 4     | MYTC = My Top Company                                                                                                                       |          |
| Environment            | 2     | Described in the chapter Affixes, Environment                                                                                               |          |
| SubscriptionID         | 4     | Ongoing numbering per environment, the first position of the number stands for: <br> 0 = Infrastructure <br> 1 = Standard <br> 2 = Special. |          |
| Product\|Service\|Team | 5..20 | CentralAutomation <br> CentralServices <br> BusinesServices <br> VDIServices <br> ExternalCorpA                                             |          |
| VersionNr              | 2     | 01..99                                                                                                                                      |          |





#### Tag







#### Ressource Group
*Pattern*: `<Prefix>_[TenantShort]_<Environment>_<Region>_<Service|System>_<VersionNr>`

*Examples*:

RSG_AU_EUWE_Automation_01\
RSG_CO_AAAA_Core_01\
RSG_CO_AAAA_Network_01\
RSG_PR_AAAA_Network_01\
RSG_PR_AAAA_Security_01\
RSG_PR_AAAA_Storage_01

RSG_MYTC_AU_EUWE_Automation_01\
RSG_MYTC_CO_AAAA_Core_01\
RSG_MYTC_CO_AAAA_Network_01\
RSG_MYTC_CO_AAAA_Security_01\
RSG_MYTC_CO_AAAA_Storage_01\
RSG_MYTC_CO_AAAA_Backup_01
RSG_MYTC_CO_EUWE_DomainServices_01
RSG_MYTC_PR_AAAA_Network_01\
RSG_MYTC_PR_AAAA_Security_01\
RSG_MYTC_PR_AAAA_Storage_01\
RSG_MYTC_PR_EUWE_ApplicationA_01\
RSG_MYTC_TE_AAAA_Network_01\
RSG_MYTC_TE_AAAA_Security_01\
RSG_MYTC_TE_AAAA_Storage_01\
RSG_MYTC_TE_EUWE_ApplicationA_01

*Description*:

| Identifiers     | Range | Values/Meaning                                             | Comments |
| --------------- | ----- | ---------------------------------------------------------- | -------- |
| Prefix          | 3     | RSG = Ressource Group                                      |          |
| TenantShort     | 4     | MYTC = My Top Company                                      |          |
| Environment     | 2     | Described in the chapter Affixes, Environment              |          |
| Region          | 4     | Described in the chapter Affixes, Region                   |          |
| Service\|System | 5..25 | Describes a purpose for which the resource should be used. |          |
| VersionNr       | 2     | 01..99                                                     |          |

*Declaration*:

Resources that are managed from the same team, and where all resources planned to be member of the same resource group, are the best examples for the AAAA Region code.

#### Virtual Network (VNet)
*Pattern*: `<Prefix>_[TenantShort]_<Region>_<Environment>_<SubscriptionID>_<VersionNr>`

*Examples*:

VNE_EUWE_CO_0001_01\
VNE_EUWE_PR_1001_01\
VNE_EUWE_TE_1002_01\
VNE_EUWE_DE_1003_01

VNE_MYTC_EUWE_CO_0001_01\
VNE_MYTC_EUWE_PR_1001_01\
VNE_MYTC_EUWE_TE_1002_01\
VNE_MYTC_EUWE_DE_1003_01

*Description*:

| Identifiers    | Range | Values/Meaning                                                            | Comments |
| -------------- | ----- | ------------------------------------------------------------------------- | -------- |
| Prefix         | 3     | VNE = Virtual Network                                                     |          |
| TenantShort    | 4     | MYTC = My Top Company                                                     |          |
| Region         | 4     | Described in the chapter Affixes, Region                                  |          |
| Environment    | 2     | Described in the chapter Affixes, Environment                             |          |
| SubscriptionID | 4     | Same SubscriptionID in which subscription the resource will be published. |          |
| VersionNr      | 2     | 01..99                                                                    |          |


#### VNet Peering
*Pattern*: `<Prefix>_[SourceTenantShort]_<SourceRegion>_<SourceEnvironment>_<SourceSubscriptionID>_<SourceVersionNr>-[TargetTenantShort]_<TargetRegion>_<TargetEnvironment>_<TargetSubscriptionID>_<TargetVersionNr>`

*Examples*:

VNP_EUWE_CO_0001_01-EUWE_PR_1001_01\
VNP_EUWE_PR_1001_01-EUWE_CO_0001_01\
VNP_EUWE_CO_0001_01-EUWE_TE_1002_01\
VNP_EUWE_TE_1002_01-EUWE_CO_0001_01\
VNP_EUWE_CO_0001_01-EUWE_DE_1003_01\
VNP_EUWE_DE_1003_01-EUWE_CO_0001_01

VNP_MYTC_EUWE_CO_0001_01-MYTC_EUWE_PR_1001_01\
VNP_MYTC_EUWE_PR_1001_01-MYTC_EUWE_CO_0001_01\
VNP_MYTC_EUWE_CO_0001_01-MYTC_EUWE_TE_1002_01\
VNP_MYTC_EUWE_TE_1002_01-MYTC_EUWE_CO_0001_01\
VNP_MYTC_EUWE_CO_0001_01-MYTC_EUWE_DE_1003_01\
VNP_MYTC_EUWE_DE_1003_01-MYTC_EUWE_CO_0001_01

*Description*:

| Identifiers    | Range | Values/Meaning                                                     | Comments |
| -------------- | ----- | ------------------------------------------------------------------ | -------- |
| Prefix         | 3     | VNP = VNet Peering                                                 |          |
| TenantShort    | 4     | MYTC = My Top Company                                              |          |
| Region         | 4     | Described in the chapter Affixes, Region                           |          |
| Environment    | 2     | Described in the chapter Affixes, Environment                      |          |
| SubscriptionID | 4     | Same SubscriptionID which is also used for the corresponding VNet. |          |
| VersionNr      | 2     | 01..99                                                             |          |


#### Subnet
*Pattern*: `<Prefix>_<Region>_<Environment>_<SubscriptionID>_[CustomerShort]_<Service|System>_<AreaShort>`

*Examples*:

SNE_EUWE_CO_0001_Frontend_FE\
SNE_EUWE_CO_0001_Backend_BE\
SNE_EUWE_CO_0001_Management_MG\
SNE_EUWE_CO_0001_DomainServices_FE\
SNE_EUWE_PR_1001_Frontend_FE\
SNE_EUWE_PR_1001_Backend_BE\
SNE_EUWE_PR_1001_Management_MG\
SNE_EUWE_PR_1001_CSTA_DMZ_FE\
SNE_EUWE_PR_1001_CSTA_DMZ_BE\
SNE_EUWE_PR_1001_CSTA_AppServer_BE\
SNE_EUWE_PR_1001_CSTB_AppServer_BE

*Description*:

| Identifiers     | Range | Values/Meaning                                                     | Comments |
| --------------- | ----- | ------------------------------------------------------------------ | -------- |
| Prefix          | 3     | VNP = VNet Peering                                                 |          |
| Region          | 4     | Described in the chapter Affixes, Region                           |          |
| Environment     | 2     | Described in the chapter Affixes, Environment                      |          |
| SubscriptionID  | 4     | Same SubscriptionID which is also used for the corresponding VNet. |          |
| CustomerShort   | 4     | Short name of the customer name, which occurs in different places. |          |
| Service\|System | 5..25 | Describes a purpose for which the resource should be used.         |          |
| AreaShort       | 2     | FE = Frontend <br> BE = Backend <br> MG = Management               |          |

#### Route Table
*Pattern*: `<Prefix>_[TenantShort]_<Region>_<Environment>_<SubscriptionID>_<VersionNr>`

*Examples*:

NRT_EUWE_CO_0001_01\
NRT_EUWE_PR_1001_01\
NRT_EUWE_TE_1002_01\
NRT_EUWE_DE_1003_01

NRT_MYTC_EUWE_CO_0001_01\
NRT_MYTC_EUWE_PR_1001_01\
NRT_MYTC_EUWE_TE_1002_01\
NRT_MYTC_EUWE_DE_1003_01


*Description*:

| Identifiers    | Range | Values/Meaning                                                     | Comments |
| -------------- | ----- | ------------------------------------------------------------------ | -------- |
| Prefix         | 3     | VNE = Virtual Network                                              |          |
| TenantShort    | 4     | MYTC = My Top Company                                              |          |
| Region         | 4     | Described in the chapter Affixes, Region                           |          |
| Environment    | 2     | Described in the chapter Affixes, Environment                      |          |
| SubscriptionID | 4     | Same SubscriptionID which is also used for the corresponding VNet. |          |
| VersionNr      | 2     | 01..99                                                             |          |


#### Network Security Group
*Pattern*: `<Prefix>_[TenantShort]_<Region>_<Environment>_<SubscriptionID>_<Service|System>_<AreaShort>`

*Examples*:

NSG_EUWE_CO_0001_Frontend_FE\
NSG_EUWE_CO_0001_Backend_BE\
NSG_EUWE_CO_0001_Management_MG\
NSG_EUWE_CO_0001_DomainServices_FE\
NSG_EUWE_PR_1001_Frontend_FE\
NSG_EUWE_PR_1001_Backend_BE\
NSG_EUWE_PR_1001_Management_MG

NSG_MYTC_EUWE_CO_0001_Frontend_FE\
NSG_MYTC_EUWE_CO_0001_Backend_BE\
NSG_MYTC_EUWE_CO_0001_Management_MG\
NSG_MYTC_EUWE_CO_0001_DomainServices_FE\
NSG_MYTC_EUWE_PR_1001_Frontend_FE\
NSG_MYTC_EUWE_PR_1001_Backend_BE\
NSG_MYTC_EUWE_PR_1001_Management_MG\
NSG_MYTC_EUWE_PR_1001_CSTA_DMZ_FE\
NSG_MYTC_EUWE_PR_1001_CSTA_DMZ_BE\
NSG_MYTC_EUWE_PR_1001_CSTA_AppServer_BE\
NSG_MYTC_EUWE_PR_1001_CSTB_AppServer_BE

*Description*:

| Identifiers     | Range | Values/Meaning                                                     | Comments |
| --------------- | ----- | ------------------------------------------------------------------ | -------- |
| Prefix          | 3     | NSG = Network Security Group                                       |          |
| TenantShort     | 4     | MYTC = My Top Company                                              |          |
| Region          | 4     | Described in the chapter Affixes, Region                           |          |
| Environment     | 2     | Described in the chapter Affixes, Environment                      |          |
| SubscriptionID  | 4     | Same SubscriptionID which is also used for the corresponding VNet. |          |
| Service\|System | 5..25 | Describes a purpose for which the resource should be used.         |          |
| AreaShort       | 2     | FE = Frontend <br> BE = Backend <br> MG = Management               |          |

*Declaration*:
Network Security Groups inherit the name of the Subnet, they are not using a counter as there can’t be multiple NSG with the same name.

#### Network Security Group Rule
*Pattern*: `<Prefix>_<Direction>_<Protocol>_<Action>_<FromToWhere|Service|System>_<ShortPortDescription>`

*Examples*:

Inbound:\
NSR_in_TCP_allow_JUMPtoVNET-RDP\
NSR_in_ANY_allow_CXCCtoVDAIP-WEB

Outbound:\
NSR_out_TCP_allow_JUMPtoVNET-RDP\
NSR_out_ANY_allow_WAPtoWAP-ANY


*Description*:

| Identifiers                  | Range | Values/Meaning                                                  | Comments                                                                                                              |
| ---------------------------- | ----- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Prefix                       | 3     | NSR = Network Security Group Rule                               |                                                                                                                       |
| Direction                    | 2..3  | in <br> out                                                     |                                                                                                                       |
| Protocol                     | 3     | ANY <br> TCP <br> UDP                                           |                                                                                                                       |
| Action                       | 4..5  | allow <br> deny                                                 |                                                                                                                       |
| FromToWhere\|Service\|System | 5..20 | JUMPtoVNET <br> CXCCtoVDAIP <br> ONPREMtoJUMP <br> WAPtoWAP     | As a rule, an abbreviation of 4 characters per service is attempted here. But this is not a hard value at the moment. |
| ShortPortDescription         | 2..8  | RDP <br> HTTP <br> HTTPS <br> ICA <br> DNS <br> WEB <br> DOMAIN |                                                                                                                       |


#### Application Security Group
*Pattern*: `<Prefix>_[TenantShort]_<Region>_<Environment>_<SubscriptionID>_<Service|System>_<VersionNr>`

*Examples*:
ASG_EUWE_CO_0001_WAP_01\
ASG_EUWE_CO_0001_ADDC_01\
ASG_EUWE_CO_0001_ADFS_01\
ASG_EUWE_CO_0001_ADCA_01\
ASG_EUWE_CO_0001_AADC_01

ASG_MYTC_EUWE_CO_0001_WAP_01\
ASG_MYTC_EUWE_CO_0001_ADDC_01\
ASG_MYTC_EUWE_CO_0001_ADFS_01\
ASG_MYTC_EUWE_CO_0001_ADCA_01\
ASG_MYTC_EUWE_CO_0001_AADC_01

*Description*:

| Identifiers     | Range | Values/Meaning                                                     | Comments |
| --------------- | ----- | ------------------------------------------------------------------ | -------- |
| Prefix          | 3     | SUB = Subscription                                                 |          |
| TenantShort     | 4     | MYTC = My Top Company                                              |          |
| Region          | 4     | Described in the chapter Affixes, Region                           |          |
| Environment     | 2     | Described in the chapter Affixes, Environment                      |          |
| SubscriptionID  | 4     | Same SubscriptionID which is also used for the corresponding VNet. |          |
| Service\|System | 5..25 | Describes a purpose for which the resource should be used.         |          |
| VersionNr       | 2     | 01..99                                                             |          |



[//]: # (This section Stefan Beckmann will create the chapters, he had some examples, that we can discuss then.)

#### Availability Set*
#### VPN Gateway*
#### Local Network Gateway*
#### Internal Load Balancer*
#### External Load Balancer*
#### Load Balancing Rules Config
#### Blueprints
#### Automation Account*
#### Recovery Service Vault*
##### Azure Backup Policy
#### Log Analytics Workspace*

#### Template
*Pattern*: `<Prefix>_<Region>_<Environment>_<VersionNr>`

*Examples*:


*Description*:

| Identifiers | Range | Values/Meaning                                | Comments |
| ----------- | ----- | --------------------------------------------- | -------- |
| Prefix      | 3     | SUB = Subscription                            |          |
| Region      | 4     | Described in the chapter Affixes, Region      |          |  |
| Environment | 2     | Described in the chapter Affixes, Environment |          |
| VersionNr   | 2     | 01..99                                        |          |

[recommendations]: # ( end )

