---
title: Funciones globales de identificador de seguridad
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: ab5d743c7c6abf7ee3a849a28916ebd32788ef40
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269414"
---
# <a name="security-identifier-global-functions"></a>Funciones globales de identificador de seguridad

Estas funciones devuelven objetos de SID conocido comunes.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Devuelve SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[Sids::Admins](#admins)|Devuelve el SID de DOMAIN_ALIAS_RID_ADMINS.|
|[Sids::AnonymousLogon](#anonymouslogon)|Devuelve el SID de SECURITY_ANONYMOUS_LOGON_RID.|
|[Sids::AuthenticatedUser](#authenticateduser)|Devuelve el SID de SECURITY_AUTHENTICATED_USER_RID.|
|[Sids::BackupOps](#backupops)|Devuelve el SID de DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Sids::Batch](#batch)|Devuelve el SID de SECURITY_BATCH_RID.|
|[Sids::CreatorGroup](#creatorgroup)|Devuelve el SID de SECURITY_CREATOR_GROUP_RID.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Devuelve el SID de SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Sids::CreatorOwner](#creatorowner)|Devuelve el SID de SECURITY_CREATOR_OWNER_RID.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Devuelve el SID de SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Sids::Dialup](#dialup)|Devuelve el SID de SECURITY_DIALUP_RID.|
|[Sids::Guests](#guests)|Devuelve el SID de DOMAIN_ALIAS_RID_GUESTS.|
|[Sids::Interactive](#interactive)|Devuelve el SID de SECURITY_INTERACTIVE_RID.|
|[Sids::Local](#local)|Devuelve el SID de SECURITY_LOCAL_RID.|
|[Sids::Network](#network)|Devuelve el SID de SECURITY_NETWORK_RID.|
|[Sids::NetworkService](#networkservice)|Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.|
|[Sids::Null](#null)|Devuelve el SID de SECURITY_NULL_RID.|
|[Sids::PreW2KAccess](#prew2kaccess)|Devuelve el SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Sids::PowerUsers](#powerusers)|Devuelve el SID de DOMAIN_ALIAS_RID_POWER_USERS.|
|[Sids::PrintOps](#printops)|Devuelve el SID de DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Sids::Proxy](#proxy)|Devuelve el SID de SECURITY_PROXY_RID.|
|[Sids::RasServers](#rasservers)|Devuelve el SID de DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[Sids::Replicator](#replicator)|Devuelve el SID de DOMAIN_ALIAS_RID_REPLICATOR.|
|[Sids::RestrictedCode](#restrictedcode)|Devuelve el SID de SECURITY_RESTRICTED_CODE_RID.|
|[Sids::Self](#self)|Devuelve el SID de SECURITY_PRINCIPAL_SELF_RID.|
|[Sids::ServerLogon](#serverlogon)|Devuelve el SID de SECURITY_SERVER_LOGON_RID.|
|[Sids::Service](#service)|Devuelve el SID de SECURITY_SERVICE_RID.|
|[Sids::System](#system)|Devuelve el SID de SECURITY_LOCAL_SYSTEM_RID.|
|[Sids::SystemOps](#systemops)|Devuelve el SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::TerminalServer](#terminalserver)|Devuelve el SID de SECURITY_TERMINAL_SERVER_RID.|
|[Sids::Users](#users)|Devuelve el SID de DOMAIN_ALIAS_RID_USERS.|
|[Sids::World](#world)|Devuelve el SID de SECURITY_WORLD_RID.|

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

Devuelve SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

Devuelve el SID de DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

Devuelve el SID de SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

Devuelve el SID de SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

Devuelve el SID de DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

Devuelve el SID de SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

Devuelve el SID de SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

Devuelve el SID de SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

Devuelve el SID de SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

Devuelve el SID de SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  SIDs::Dialup

Devuelve el SID de SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  SIDs::Guests

Devuelve el SID de DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

Devuelve el SID de SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

Devuelve el SID de SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

Devuelve el SID de SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Comentarios

Utilizar NetworkService para permitir que el usuario de NT AUTHORITY\NetworkService leer un objeto de seguridad CPerfMon. NetworkService, agrega un SecurityAttribute en el código de servidor ATL que permitirá que el archivo DLL para el inicio de sesión con la cuenta NetworkService en Windows XP Home Edition, Windows XP Professional, Windows Server 2003 y sistema operativo mayor.

Cuando se crean los contadores de registro personalizado con la clase ATLServer CPerfMon en Perfmon MMC, los contadores no pueden aparecer al ver el archivo de registro aunque aparezcan correctamente en la vista en tiempo real. Contadores de rendimiento personalizados CPerfMon no tienen los permisos necesarios para ejecutar en el servicio de "Registros y alertas de rendimiento" (smlogsvc.exe) en Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (o superior) los sistemas operativos. Este servicio se ejecuta bajo la cuenta "NT AUTHORITY\NetworkService".

##  <a name="null"></a>  Sids::Null

Devuelve el SID de SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

Devuelve el SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

Devuelve el SID de DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

Devuelve el SID de DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  SIDs::proxy

Devuelve el SID de SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

Devuelve el SID de DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  SIDs::Replicator

Devuelve el SID de DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

Devuelve el SID de SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  SIDs::Self

Devuelve el SID de SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

Devuelve el SID de SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

Devuelve el SID de SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

Devuelve el SID de SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

Devuelve el SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

Devuelve el SID de SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

Devuelve el SID de DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

Devuelve el SID de SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
