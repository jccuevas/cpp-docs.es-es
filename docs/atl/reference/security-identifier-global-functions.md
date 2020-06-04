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
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325996"
---
# <a name="security-identifier-global-functions"></a>Funciones globales de identificador de seguridad

Estas funciones devuelven objetos SID conocidos comunes.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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
|[SIDs::NetworkService](#networkservice)|Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.|
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

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids::AccountOps

Devuelve SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids::Admins

Devuelve el SID de DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::AnonymousLogon

Devuelve el SID de SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::AuthenticatedUser

Devuelve el SID de SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids::BackupOps

Devuelve el SID de DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids::Batch

Devuelve el SID de SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::CreatorGroup

Devuelve el SID de SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::CreatorGroupServer

Devuelve el SID de SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids::CreatorOwner

Devuelve el SID de SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::CreatorOwnerServer

Devuelve el SID de SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>Sids::Dialup

Devuelve el SID de SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>Sids::Invitados

Devuelve el SID de DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids::Interactivo

Devuelve el SID de SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids::Local

Devuelve el SID de SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids::Red

Devuelve el SID de SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids::NetworkService

Devuelve el SID de SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Observaciones

Utilice NetworkService para permitir que el usuario NT AUTHORITY-NetworkService lea un objeto de seguridad CPerfMon. NetworkService agrega un SecurityAttribute al código ATLServer que permitirá que el archivo DLL inicie sesión en la cuenta NetworkService en Windows XP Home Edition, Windows XP Professional, Windows Server 2003 y un sistema operativo superior.

Cuando se crean contadores de registro personalizados con la clase ATLServer CPerfMon en la MMC de Perfmon, es posible que los contadores no aparezcan al ver el archivo de registro aunque aparecerán correctamente en la vista en tiempo real. Los contadores de rendimiento personalizados de CPerfMon no tienen los permisos necesarios para ejecutarse en el servicio "Registros y alertas de rendimiento" (smlogsvc.exe) en los sistemas operativos Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (o superior). Este servicio se ejecuta bajo la cuenta "NT AUTHORITY-NetworkService".

## <a name="sidsnull"></a><a name="null"></a>Sids::Null

Devuelve el SID de SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess

Devuelve el SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids::PowerUsers

Devuelve el SID de DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>Sids::PrintOps

Devuelve el SID de DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>Sids::Proxy

Devuelve el SID de SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids::RasServers

Devuelve el SID de DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids::Replicator

Devuelve el SID de DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::RestrictedCode

Devuelve el SID de SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>Sids::Self

Devuelve el SID de SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids::ServerLogon

Devuelve el SID de SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>Sids::Servicio

Devuelve el SID de SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids::Sistema

Devuelve el SID de SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids::SystemOps

Devuelve el SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids::TerminalServer

Devuelve el SID de SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids::Usuarios

Devuelve el SID de DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>Sids::Mundo

Devuelve el SID de SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
