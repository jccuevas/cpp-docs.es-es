---
title: Funciones globales del identificador de seguridad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 9e51fe30b0519514df34f1a77b1e731f51047520
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="security-identifier-global-functions"></a>Funciones globales del identificador de seguridad
Estas funciones devuelven objetos de SID conocido comunes.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[SIDs::AccountOps](#accountops)|Devuelve SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.|  
|[SIDs::Admins](#admins)|Devuelve el SID de DOMAIN_ALIAS_RID_ADMINS.|  
|[SIDs::AnonymousLogon](#anonymouslogon)|Devuelve el SID de SECURITY_ANONYMOUS_LOGON_RID.|  
|[SIDs::AuthenticatedUser](#authenticateduser)|Devuelve el SID de SECURITY_AUTHENTICATED_USER_RID.|  
|[SIDs::BackupOps](#backupops)|Devuelve el SID de DOMAIN_ALIAS_RID_BACKUP_OPS.|  
|[SIDs::Batch](#batch)|Devuelve el SID de SECURITY_BATCH_RID.|  
|[SIDs::CreatorGroup](#creatorgroup)|Devuelve el SID de SECURITY_CREATOR_GROUP_RID.|  
|[SIDs::CreatorGroupServer](#creatorgroupserver)|Devuelve el SID de SECURITY_CREATOR_GROUP_SERVER_RID.|  
|[SIDs::CreatorOwner](#creatorowner)|Devuelve el SID de SECURITY_CREATOR_OWNER_RID.|  
|[SIDs::CreatorOwnerServer](#creatorownerserver)|Devuelve el SID de SECURITY_CREATOR_OWNER_SERVER_RID.|  
|[SIDs::Dialup](#dialup)|Devuelve el SID de SECURITY_DIALUP_RID.|  
|[SIDs::Guests](#guests)|Devuelve el SID de DOMAIN_ALIAS_RID_GUESTS.|  
|[SIDs::Interactive](#interactive)|Devuelve el SID de SECURITY_INTERACTIVE_RID.|  
|[SIDs::local](#local)|Devuelve el SID de SECURITY_LOCAL_RID.|  
|[SIDs::Network](#network)|Devuelve el SID de SECURITY_NETWORK_RID.|  
|[SIDs::NetworkService](#networkservice)|Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.|  
|[SIDs::null](#null)|Devuelve el SID de SECURITY_NULL_RID.|  
|[SIDs::PreW2KAccess](#prew2kaccess)|Devuelve el SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|  
|[SIDs::PowerUsers](#powerusers)|Devuelve el SID de DOMAIN_ALIAS_RID_POWER_USERS.|  
|[SIDs::PrintOps](#printops)|Devuelve el SID de DOMAIN_ALIAS_RID_PRINT_OPS.|  
|[SIDs::proxy](#proxy)|Devuelve el SID de SECURITY_PROXY_RID.|  
|[SIDs::RasServers](#rasservers)|Devuelve el SID de DOMAIN_ALIAS_RID_RAS_SERVERS.|  
|[SIDs::Replicator](#replicator)|Devuelve el SID de DOMAIN_ALIAS_RID_REPLICATOR.|  
|[SIDs::RestrictedCode](#restrictedcode)|Devuelve el SID de SECURITY_RESTRICTED_CODE_RID.|  
|[SIDs::Self](#self)|Devuelve el SID de SECURITY_PRINCIPAL_SELF_RID.|  
|[SIDs::ServerLogon](#serverlogon)|Devuelve el SID de SECURITY_SERVER_LOGON_RID.|  
|[SIDs::Service](#service)|Devuelve el SID de SECURITY_SERVICE_RID.|  
|[SIDs::System](#system)|Devuelve el SID de SECURITY_LOCAL_SYSTEM_RID.|  
|[SIDs::SystemOps](#systemops)|Devuelve el SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.|  
|[SIDs::terminalserver](#terminalserver)|Devuelve el SID de SECURITY_TERMINAL_SERVER_RID.|  
|[SIDs::Users](#users)|Devuelve el SID de DOMAIN_ALIAS_RID_USERS.|  
|[SIDs::World](#world)|Devuelve el SID de SECURITY_WORLD_RID.|  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h 

##  <a name="accountops"></a>SIDs::AccountOps  
 Devuelve SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.    
  
```
CSid AccountOps() throw(...);
```  
  
##  <a name="admins"></a>SIDs::Admins  
 Devuelve el SID de DOMAIN_ALIAS_RID_ADMINS.  
```
CSid Admins() throw(...);
```  
  
##  <a name="anonymouslogon"></a>SIDs::AnonymousLogon  
 Devuelve el SID de SECURITY_ANONYMOUS_LOGON_RID.  
```
CSid AnonymousLogon() throw(...);
```  
  
##  <a name="authenticateduser"></a>SIDs::AuthenticatedUser  
 Devuelve el SID de SECURITY_AUTHENTICATED_USER_RID.  
```
CSid AuthenticatedUser() throw(...);
```  
  
##  <a name="backupops"></a>SIDs::BackupOps  
 Devuelve el SID de DOMAIN_ALIAS_RID_BACKUP_OPS.  
```
CSid BackupOps() throw(...);
```  
  
##  <a name="batch"></a>SIDs::Batch  
 Devuelve el SID de SECURITY_BATCH_RID.  
```
CSid Batch() throw(...);
```  
  
##  <a name="creatorgroup"></a>SIDs::CreatorGroup  
 Devuelve el SID de SECURITY_CREATOR_GROUP_RID.  
```
CSid CreatorGroup() throw(...);
```  
  
##  <a name="creatorgroupserver"></a>SIDs::CreatorGroupServer  
 Devuelve el SID de SECURITY_CREATOR_GROUP_SERVER_RID.  
```
CSid CreatorGroupServer() throw(...);
```  
  
##  <a name="creatorowner"></a>SIDs::CreatorOwner  
 Devuelve el SID de SECURITY_CREATOR_OWNER_RID.  
```
CSid CreatorOwner() throw(...);
```  
  
##  <a name="creatorownerserver"></a>SIDs::CreatorOwnerServer  
 Devuelve el SID de SECURITY_CREATOR_OWNER_SERVER_RID.  
```
CSid CreatorOwnerServer() throw(...);
```  
  
##  <a name="dialup"></a>SIDs::Dialup  
 Devuelve el SID de SECURITY_DIALUP_RID.  
```
CSid Dialup() throw(...);
```  
  
##  <a name="guests"></a>SIDs::Guests  
 Devuelve el SID de DOMAIN_ALIAS_RID_GUESTS.  
```
CSid Guests() throw(...);
```  
  
##  <a name="interactive"></a>SIDs::Interactive  
 Devuelve el SID de SECURITY_INTERACTIVE_RID.  
```
CSid Interactive() throw(...);
```  
  
##  <a name="local"></a>SIDs::local  
 Devuelve el SID de SECURITY_LOCAL_RID.  
```
CSid Local() throw(...);
```  
  
##  <a name="network"></a>SIDs::Network  
 Devuelve el SID de SECURITY_NETWORK_RID.  
```
CSid Network() throw(...);
```  
  
##  <a name="networkservice"></a>SIDs::NetworkService  
 Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.  
```
CSid NetworkService() throw(...);
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice NetworkService para permitir que el usuario de NT AUTHORITY\NetworkService leer un objeto de seguridad de CPerfMon. NetworkService agrega un SecurityAttribute al código de servidor ATL que le permitirá iniciar sesión con la cuenta NetworkService en la DLL [!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)] y mayor sistema operativo.  
  
 Cuando se crean contadores de registro personalizado con la clase ATLServer CPerfMon en MMC Perfmon, los contadores no pueden aparecer al ver el archivo de registro aunque aparezcan correctamente en la vista en tiempo real. Contadores de rendimiento personalizados CPerfMon no tienen los permisos necesarios para ejecutarse en el servicio de "Registros y alertas de rendimiento" (smlogsvc.exe) en [!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)] (o posterior) sistemas operativos. Este servicio se ejecuta bajo la cuenta "NT AUTHORITY\NetworkService".  
  
##  <a name="null"></a>SIDs::null  
 Devuelve el SID de SECURITY_NULL_RID.  
```
CSid Null() throw(...);
```  
  
##  <a name="prew2kaccess"></a>SIDs::PreW2KAccess  
 Devuelve el SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.  
```
CSid PreW2KAccess() throw(...);
```  
  
##  <a name="powerusers"></a>SIDs::PowerUsers  
 Devuelve el SID de DOMAIN_ALIAS_RID_POWER_USERS.  
```
CSid PowerUsers() throw(...);
```  
  
##  <a name="printops"></a>SIDs::PrintOps  
 Devuelve el SID de DOMAIN_ALIAS_RID_PRINT_OPS.  
```
CSid PrintOps() throw(...);
```  
  
##  <a name="proxy"></a>SIDs::proxy  
 Devuelve el SID de SECURITY_PROXY_RID.  
```
CSid Proxy() throw(...);
```  
  
##  <a name="rasservers"></a>SIDs::RasServers  
 Devuelve el SID de DOMAIN_ALIAS_RID_RAS_SERVERS.  
```
CSid RasServers() throw(...);
```  
  
##  <a name="replicator"></a>SIDs::Replicator  
 Devuelve el SID de DOMAIN_ALIAS_RID_REPLICATOR.  
```
CSid Replicator() throw(...);
```  
  
##  <a name="restrictedcode"></a>SIDs::RestrictedCode  
 Devuelve el SID de SECURITY_RESTRICTED_CODE_RID.  
```
CSid RestrictedCode() throw(...);
```  
  
##  <a name="self"></a>SIDs::Self  
 Devuelve el SID de SECURITY_PRINCIPAL_SELF_RID.  
```
CSid Self() throw(...);
```  
  
##  <a name="serverlogon"></a>SIDs::ServerLogon  
 Devuelve el SID de SECURITY_SERVER_LOGON_RID.  
```
CSid ServerLogon() throw(...);
```  
  
##  <a name="service"></a>SIDs::Service  
 Devuelve el SID de SECURITY_SERVICE_RID.  
```
CSid Service() throw(...);
```  
  
##  <a name="system"></a>SIDs::System  
 Devuelve el SID de SECURITY_LOCAL_SYSTEM_RID.  
```
CSid System() throw(...);
```  
  
##  <a name="systemops"></a>SIDs::SystemOps  
 Devuelve el SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.  
```
CSid SystemOps() throw(...);
```  
  
##  <a name="terminalserver"></a>SIDs::terminalserver  
 Devuelve el SID de SECURITY_TERMINAL_SERVER_RID.  
```
CSid TerminalServer() throw(...);
```  
  
##  <a name="users"></a>SIDs::Users  
 Devuelve el SID de DOMAIN_ALIAS_RID_USERS.  
```
CSid Users() throw(...);
```  
  
##  <a name="world"></a>SIDs::World  
 Devuelve el SID de SECURITY_WORLD_RID.  
```
CSid World() throw(...);
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

