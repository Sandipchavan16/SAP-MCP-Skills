---
name: sap-naming-conventions
description: Apply SAP ABAP naming conventions when writing, reviewing, or generating SAP development objects. Use this skill whenever the user asks about naming SAP objects, reviews ABAP code, creates CDS views, RAP objects, DDIC objects, FIORI/UI5 apps, WebDynpro components, BRF+ rules, BOBF business objects, or any custom SAP Z/Y development. Trigger on keywords like "ABAP", "SAP", "CDS", "RAP", "DDIC", "FIORI", "BAdI", "function module", "class", "interface", "database table", "naming convention", or any request to name or validate a SAP development object.
---

# SAP ABAP Naming Convention Guidelines

Use this skill to correctly name any SAP custom development object. All custom objects use `Z` (transportable) or `Y` (local/sandbox) prefixes.

---

## Module Prefixes (`<MD>`)

| Module | Prefix |
|---|---|
| Cross-Module | `CMNN` |
| Accounts to Report | `A2R` |
| Procure to Pay | `P2P` |
| Order to Cash | `O2C` |
| Service Delivery | `SD` |
| Lead to Agreement | `L2A` |

**Criticality codes (`<C>`):** `C` = Critical, `N` = Not Critical

---

## General & DDIC Objects

### Packages & General
| Object | Pattern | Example |
|---|---|---|
| Package | `Z<MD>` | `ZO2C` |
| Package for UI/FIORI | `Z<MD>_UI` | `ZO2C_UI` |
| Package for Interface | `Z<MD>_INF` | `ZO2C_INF` |
| Message Class | `Z<n>` | `ZFREIGHT_ORDER` |
| Transaction Code | `Z<MD><C>_<n>` | `ZSDC_ASSIGN_RECEPIENT` |
| Area Menu | `ZTM_<MD>_<n>` | `ZTM_O2C_Administration_Support` |

### Dictionary (DDIC) Objects
| Object | Pattern | Example | Notes |
|---|---|---|---|
| Database Table | `ZD<DT>_<n>[T]` | `ZDD_TRQPTY` | `<DT>`: C=Customizing, D=Transaction, M=Master; `[T]`=Text Table |
| Views | `ZV<VT>_<n>` | `ZVP_TRQPTY` | `<VT>`: D=Database, P=Projection, H=Help, M=Maintenance |
| Data Element | `Z<n>` | `ZTRQPTY` | |
| Structure | `ZST_<n>` | `ZST_TRQPTY` | |
| Table Type | `ZT_<n>` | `ZT_TRQPTY` | |
| Domain | `Z<n>` | `ZTRQPTY` | |
| Search Help | `Z<n>` | `ZTRQPTY` | |
| Lock Object | `EZ_<n>` | `EZAOD_TAGLIB` | |
| DDL Definition (CDS) | `Z<VT>_<n>` | `ZI_TransportationOrder` | `<VT>`: I=Interface, R=Root/Base, C=Projection, A=Abstract, CE=Custom Entity |
| DCL Definition | `Z<VT>_<n>` | `ZI_TransportationOrder` | Same name as DDL. All CDS Views must have Access Control. |
| SQL Database View | `ZSQL<VT>_<n>` | `ZSQLITRANSPORDER` | Prefer `Define View Entity` instead |

### Enhancements
| Object | Pattern | Example |
|---|---|---|
| Enhancement Spot | `ZES_<n>` | `ZES_CARRIER_FACTOR` |
| Composite Enhancement Spot | `ZCES_<n>` | `ZCES_CARRIER_FACTOR` |
| BAdI Definition | `ZBD_<n>` | `ZBD_CARRIER_FACTOR` |
| BAdI Implementation | `ZBI_<n>` | `ZBI_CARRIER_FACTOR` |
| Enhancement Implementation | `ZEI_<n>` | `ZEI_CARRIER_FACTOR` |
| Composite Enh. Implementation | `ZCEI_<n>` | `ZCEI_CARRIER_FACTOR` |
| Project (CMOD) | `Z<n>` | `ZVENDINV` (max 8 chars) |
| Append Structure | `ZZ<n>` | `ZZFWO_INTREF` |
| Field in Append | `ZZ<n>` | `ZZEXT_ITMREF` |

### IDoc
| Object | Pattern | Example |
|---|---|---|
| IDoc Extension | `Z<basic_type>EXT` | `ZARTMAS05EXT` |
| IDoc Segment | `Z<n>` | `ZARTMASAPPEND` |
| IDoc | `Z<n>` | `ZARTMAS05` |
| Message Type | `Z<n>` | `ZARTMAS` |
| Partner Profile | `<Logical System Name>` | `NS1CLNT100` |

### Authorisations
| Object | Pattern | Example | Notes |
|---|---|---|---|
| Class | `Z<MD>` | `ZO2C` | |
| Object | `Z<MD>_<n>` | `ZSD_LAST_MILE` | |
| Auth Groups for Tables (14 chars) | `Z<MD><C>_<n>` | `ZSDC_MRE` | |
| Client Specific Auth Groups (4 chars) | `Z<M><n>` | `ZSO1` | `<M>`: one char module name |
| Auth Groups for Programs (8 chars) | `Z<MD>_<n>` | `ZOTC_CHG` | |

---

## ABAP & OO ABAP

### Global Objects (SE24)
| Object | Pattern | Example | Notes |
|---|---|---|---|
| Class | `ZCL_<type>_<n>` | `ZCL_TVARVC_CONFIGURATION` | `<type>`: optional, e.g. `CQ` for Custom Query |
| Exception Class | `ZCX_<n>` | `ZCX_INVALID_CONFIGURATION` | |
| Interface | `ZIF_<n>` | `ZIF_CONFIGURABLE` | |
| Report | `Z<MD><C>_<n>` | `ZATRC_CREATE_BOOKINGS_XLS` | |
| Includes | `Z<n>` or `MZ<n>` | `ZDEPO_CHANGES_F01` | |
| Module Pool | `SAPMZ<n>` | | |
| Function Group | `Z<MD>_<n>` | `ZSD_OPTIMIZER` | |
| Function Group (table maintenance) | Same as Maintenance View | | |
| Function Module | `Z<MD><C>_<n>` | `ZSDC_OPTIMIZER` | |
| Dynpro Numbers | `9000–9999` | | |

### Internal Declarations (within classes/programs)
| Object | Pattern | Example | Notes |
|---|---|---|---|
| Constants | `CO_<n>` or enum pattern | `co_gcss_identifier` | Prefer Clean ABAP enumerations |
| Types (structure) | `TY_<n>` | `ty_transportation_order` | |
| Types (table type) | `TT_<n>` | `tt_transportation_order` | |
| Instance/Static Attributes | `<n>` | `transportation_orders` | Singular for vars/structures, plural for tables |
| Data (global) | `<n>` | `transportation_order_id` | Avoid global declarations |
| Local Class | `lcl_<n>` | `lcl_shipper` | |
| Local Interface | `lif_<n>` | `lif_switchable` | |
| Local Test Class | `ltc_<n>` | `ltc_shipper` | |
| Local Exception Class | `lcx_<n>` | `lcx_not_found` | |

### Selection Screen
| Object | Pattern | Example |
|---|---|---|
| Parameter | `p_<n>` | `p_busptr` |
| Checkbox | `c_<n>` | `c_test` |
| Radiobutton Group | `<n>` (max 4 chars) | |
| Radiobutton | `r_<n>` | `r_print` |
| Select-options | `s_<n>` | `s_torids` |
| Selection Screen Block | `b_<n>` | `b_sc` |
| Field Symbols | `<<n>>` | `<shipper>` |

### Method Naming Patterns
| Purpose | Pattern | Example |
|---|---|---|
| SET/GET attribute access | `SET_<attr>` / `GET_<attr>` | `SET_TOR_TYPE`, `GET_ID` |
| Event handling | `ON_<event>` | `ON_DOCUMENT_CANCELLED` |
| Type conversion | `AS_<new_type>` | `AS_STRING` |
| Boolean result | `IS_<adjective>` | `IS_EMPTY`, `IS_ACTIVE` |
| Checks | `CHECK_<objective>` | `CHECK_AUTHORISATION` |

### Parameters (Function Modules / Methods)
| Type | Pattern | Example | Notes |
|---|---|---|---|
| Import | `I_<n>` | `i_company_code_number` | Aim for < 3 parameters |
| Export | `E_<n>` | `e_tor_uuid` | Only one Export/Changing/Returning |
| Table (FM only) | `T_<n>` | `t_freight_order` | |
| Changing | `C_<n>` | `c_out` | Only one Export/Changing/Returning |
| Returning | `R_<n>` | `r_result` | Only one Export/Changing/Returning |

---

## RAP (RESTful Application Programming)

| Object | Pattern | Example | Notes |
|---|---|---|---|
| Behaviour Definition | `Z<VT>_<n>` | `ZI_TransportationOrder` | Same name as root entity |
| Behaviour Pool | `ZCL_BP_<n>` | `ZCL_BP_TransportationOrder` | |
| Local Handler Class | `LHC_<n>` or `<n>` | `lhc_transportation_order` | |
| Local Saver Class | `LSC_<n>` or `<n>` | `lsc_transportation_order` | |
| Metadata Extension | `Z<VT>_<n>` | `ZC_TransportationOrder` | Same name as CDS entity |
| Service Definition | `Z<ST>_<n>` | `ZUI_TransportationOrder` | `<ST>`: UI or API |
| Service Binding | `Z<ST>_<n>_<PC>` | `ZUI_TransportationOrder_O4` | `<PC>`: O2=OData V2, O4=OData V4 |

---

## BOBF (Business Object Processing Framework)

### Business Object Objects
| Object | Pattern | Example |
|---|---|---|
| BO Enhancement Object | `ZENH_<n>` | `ZENH_TOR` |
| BO Node | `Z<n>` | `ZBENEFIT_METRIC` |
| Data Structure | `ZST_<n>` | `ZST_TOR_BENEFIT_METRIC` |
| Data Structure (transient) | `ZST_<n>_TR` | `ZST_TOR_BENEFIT_METRIC_TR` |
| Combined Node Data Structure | `ZST_<n>_K` | `ZST_TOR_BENEFIT_METRIC_K` |
| Combined Node Table Type | `ZT_<n>_K` | `ZT_TOR_BENEFIT_METRIC_K` |
| Node Extension Include | `ZST_EEW_<n>` | `ZST_EEW_TOR_BENEFIT_METRIC` |
| BO Database Table | `ZD<DT>_<n>` | `ZDD_TOR_BENMETRIC` |
| Action | `Z<n>` | `ZOPTIMIZE` |
| Determination | `Z<n>` | `ZADMIN_DATA` |
| Validation | `Z<n>` | `ZBENEFIT_METRIC_UOM` |
| Query | `Z<n>` | `ZBENEFIT_METRIC_BY_ATTR` |
| Class for Action | `ZCL_A_<n>` | `ZCL_A_BENEFIT_METRIC_OPTIMIZE` |
| Class for Determination | `ZCL_D_<n>` | `ZCL_D_TOR_ROOT_BS` |
| Class for Validation | `ZCL_V_<n>` | `ZCL_V_BENEFIT_METRIC_UOM` |
| Class for Query | `ZCL_Q_<n>` | `ZCL_Q_BENEFIT_METRY_BY_ATTR` |

### Special Class Types (UI)
| Object | Pattern | Example |
|---|---|---|
| Controller common | `ZCL_UI_<n>_CONTROLLER` | `ZCL_UI_PLN_CONTROLLER` |
| View exit | `ZCL_UI_VIEWEXIT_<n>` | `ZCL_UI_VIEWEXIT_TOR` |
| UI Helper | `ZCL_UI_HELPER_<n>` | `ZCL_UI_HELPER_TOR` |
| Conversion | `ZCL_UI_CONVERSION_<n>` | `ZCL_UI_CONVERSION_TOR` |
| IDR | `ZCL_UI_<n>_IDR` | `ZCL_UI_TOR_IDR` |
| Tab exit | `ZCL_UI_TABEXIT_<n>` | `ZCL_UI_TABEXIT_TOR` |
| Navigation | `ZCL_UI_NAV_<n>` | `ZCL_UI_NAV_TOR` |
| POWL | `ZCL_UI_POW_<n>` | `ZCL_UI_POW_TOR` |
| Common helper | `ZCL_<n>_HELPER` | `ZCL_TOR_HELPER` |
| Bootstrap | `ZCL_<n>_BOOTSTRAP` | `ZCL_TOR_BOOTSTRAP` |
| Document Flow | `ZCL_<n>_DOC_FLOW` | `ZCL_TOR_DOC_FLOW` |
| Field control | `ZCL_<n>_FC` | `ZCL_TOR_FC` |
| Exception | `ZCX_<n>` | `ZCX_DOCUMENT_NOT_FOUND` |

### Conditions
| Object | Pattern | Example |
|---|---|---|
| Condition | `ZCOND_<n>[_<variation>]` | `ZCOND_CHACO_FO` |
| Condition Type | `Z_<object>_<attribute>` | `Z_TOR_MOT` |
| Data Access Definition | `Z_<object>_<attribute>` | `Z_TOR_CATEGORY` |

---

## FIORI / UI5

| Object | Pattern | Example | Notes |
|---|---|---|---|
| UI Header Package | `ZUI` | `ZUI` | |
| UI Common Subpackage | `ZUI_COMMON` | `ZUI_COMMON` | Stores common artifacts |
| UI Subpackages | `ZUI_<UIAppShortName>` | `ZUI_SOCREATE` | |
| Project Namespace | `mycompany.<MD>.<AppDesc>` | `maersk.o2c.socreateapp` | Reverse DNS format |
| Custom/Freestyle App | `ZUI_<AppDesc>` | `ZUI_SOCREATE` | |
| Adaptation/Extension App | `ZADP_<AppDesc>` | `ZADP_SOCREATE` | |
| Semantic Object | `#Z<businessEntity>` | `#ZSalesOrder` | |
| Git Repository Name | `ZUI_<AppDesc>` | `ZUI_SOCREATE` | Same as BSP App Name |

---

## WebDynpro

### Components & Applications
| Object | Pattern | Example |
|---|---|---|
| WD Application | `Z<MD>_<n>` or `Z<MD>_<n>_<variant>` | `ZPUR_VENDOR_OVERVIEW` |
| WD Component | `Z_<n>` | `Z_OVERVIEW` |
| WD App Configuration | `<WD App name>_<variant>` | `ZSOF_LAST_MILE_OVP_GB` |
| WD Component Configuration | `ZWDCC_<n>` | |
| WD FBI View | `ZWDCC_FBI_V_<n>` | |
| Custom Controller | `CC_<n>` | |
| Window | `W_<n>` | `W_ORGANIZER` |
| View | `V_<n>` | `V_HEADER` |
| Component Usage | `U_<used_component>` | `U_EXCEPTION_POPUP` |
| Inbound Plug | `IP_<n>` | `IP_DEFAULT` |
| Outbound Plug | `OP_<n>` | `OP_EXIT` |
| Event | `E_<n>` | |

### View Elements
| Element | Pattern | Example |
|---|---|---|
| BusinessGraphics | `BGR_<n>` | `BGR_SALES` |
| Button | `BTN_<n>` | `BTN_SAVE` |
| ButtonRow | `BTR_<n>` | `BTR_DETAILS` |
| Caption | `CPT_<n>` | `CPT_COLUMN` |
| Checkbox | `CHK_<n>` | `CHK_ERRORLOG` |
| DropDownByIndex | `DDI_<n>` | `DDI_COUNTRY` |
| DropDownByKey | `DDK_<n>` | `DDK_REGION` |
| FileUpload | `FUD_<n>` | `FUD_CONTRACT` |
| Group | `GRP_<n>` | `GRP_FORM` |
| InputField | `INP_<n>` | `INP_NAME` |
| Label | `LBL_<n>` | `LBL_INPUT` |
| LinkToAction | `LTA_<n>` | `LTA_SEARCH` |
| LinkToURL | `LTU_<n>` | `LTU_VENDOR` |
| RadioButton | `RBT_<n>` | `RBT_MALE` |
| RadioButtonGroupByIndex | `RBI_<n>` | `RBI_GENDER` |
| RadioButtonGroupByKey | `RBK_<n>` | `RBK_TYP` |
| RoadMap | `RMP_<n>` | `RMP_DIMENSIONS` |
| RoadMapStep | `STP_<n>` | `STP_DIMENSION` |
| Table | `TBL_<n>` | `TBL_ADDRESS` |
| TextEdit | `TXE_<n>` | `TXE_INFO` |
| TextView | `TXV_<n>` | `TXV_INTRO` |
| TransparentContainer | `TCO_<n>` | `TCO_TABLE` |
| Tray | `TRY_<n>` | `TRY_FORM` |
| Tree | `TRE_<n>` | `TRE_SIMPLE` |
| TreeNodeType | `TNT_<n>` | `TNT_FOLDER` |
| TreeItemType | `TIT_<n>` | `TIT_FILE` |
| ViewContainerUIElement | `VCU_<n>` | `VCU_ROADMAP` |

---

## BRF+ (Business Rule Framework Plus)

### Main Object Types
| Object | Pattern | Example |
|---|---|---|
| Application | `ZA_<n>` | `ZA_DETERMINE_CONTACT_PERSON` |
| Function | `ZF_<n>` | `ZF_CONTACT_PERSON` |
| Ruleset | `ZRS_<n>` | `ZRS_CHECK_CIN` |
| Rule | `ZR_<n>` | `ZR_CHECK_CIN_EFFECTIVE_DATE` |
| Catalogs | `ZC_<n>` | `ZC_TOR` |
| Object Filters | `ZOF_<n>` | `ZOF_TOR` |

### Data Object Types
| Object | Pattern | Example |
|---|---|---|
| Data Element (any) | `ZE_<n>` | `ZE_COUNTRY_KEY` |
| Data Structure (any) | `ZS_<n>` | `ZS_COUNTRY` |
| Data Table (any) | `ZT_<n>` | `ZT_COUNTRIES` |

### Expression Types
| Object | Pattern | Example |
|---|---|---|
| Boolean | `ZB_<n>` | `ZB_ACTIVE` |
| Business Object Node | `ZBO_<n>` | `ZBO_TOR_ROOT` |
| Constant | `ZCO_<n>` | `ZCO_ROAD_FREIGHT_ORDER_TYPE` |
| Table Operation | `ZTO_<n>` | `ZTO_HAS_AT_LEAST_ONE` |
| Case | `ZCA_<n>` | `ZCA_PROCESS_BY_TOR_TYPE` |
| Database Lookup | `ZDL_<n>` | `ZDL_READ_COMPANY_DESCRIPTION` |
| Decision Table | `ZDT_<n>` | `ZDT_CONTACT_PERSON` |
| Decision Tree | `ZDR_<n>` | `ZDR_CONTACT_PERSON` |
| Formula | `ZFO_<n>` | `ZFO_DISCOUNT` |
| Function Call | `ZFC_<n>` | `ZFC_CALCULATE_TAX` |
| Loop | `ZL_<n>` | `ZL_WHILE_NEEDS_PLANNING` |
| Procedure Call | `ZP_<n>` | `ZP_TOR_CALCUALTE_CHARGES` |
| Step Sequence | `ZSS_<n>` | `ZSS_TOR_REPROCESS` |
| Value Range | `ZVR_<n>` | `ZVR_WEIGHT` |
| XSL Transformation | `ZXSL_<n>` | `ZXSL_WSDL_TRANSFORM` |

### Actions
| Object | Pattern | Example |
|---|---|---|
| Procedure Call | `ZPC_<n>` | `ZPC_TOR_CALCULATE_CHARGES` |
| Log Message | `ZLM_<n>` | `ZLM_ERROR_MESSAGE` |
| Send Email | `ZSE_<n>` | `ZSE_NOTIFICATION_TO_CARRIER` |
| Start Workflow | `ZSW_<n>` | `ZSW_PO_APPROVAL` |
| Workflow Event | `ZWE_<n>` | `ZWE_REJECT_PO` |

---

## Launchpad

| Object | Pattern | Example | Notes |
|---|---|---|---|
| Tile Information Field | `<MD><C>_<T>_<n>` | `OTCC_C_Upload Container Files` | `<T>`: C=Custom, S=Standard |
| Catalogue | `ZCAT_<MD>_<#>_<n>` | `ZCAT_ATR_1005_MACCRUALRPTUT` | `<#>`: Next sequential number |
| Group | `ZGRP_<MD>_<#>_<n>` | `ZGRP_ATR_1005_MACCRUALRPTUT` | `<#>`: Next sequential number |

---

## Key Rules & Reminders

- **Z = Transportable**, **Y = Local/Sandbox** — always use Z for production objects
- CDS views must always have an associated **DCL (Access Control)** definition
- Basic CDS views must have at minimum a `S_TABU_DIS` authority check with `ACTVT = '03'`
- Use **singular** names for variables and structures, **plural** for internal tables
- Function modules and methods should have **only one** Export, Changing, or Returning parameter
- Avoid global data declarations in classes
- Avoid macros in ABAP
- Prefer `Define View Entity` over `Define View` for CDS
