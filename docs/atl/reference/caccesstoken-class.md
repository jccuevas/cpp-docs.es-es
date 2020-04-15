---
title: Clase CAccessToken
ms.date: 07/02/2019
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: 9ae63946dfa6244e97c376f9eccd9bab93586990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319035"
---
# <a name="caccesstoken-class"></a>Clase CAccessToken

Esta clase es un contenedor para un token de acceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAccessToken
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccessToken::-CAccessToken](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|Llame a este método para tomar posesión del identificador de token de acceso especificado.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Llame a este método para determinar si un `CAccessToken` SID especificado está habilitado en el objeto.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Llame a este método para crear un nuevo token de acceso de suplantación.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Llame a este método para crear un nuevo token principal.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Llame a este método para crear un nuevo proceso que `CAccessToken` se ejecuta en el contexto de seguridad del usuario representado por el objeto.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Llame a este método para `CAccessToken` crear un nuevo objeto restringido.|
|[CAccessToken::Detach](#detach)|Llame a este método para revocar la propiedad del token de acceso.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Llame a este método para `CAccessToken` deshabilitar un privilegio en el objeto.|
|[CAccessToken::Dprivilegiosables](#disableprivileges)|Llame a este método para deshabilitar `CAccessToken` uno o varios privilegios en el objeto.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Llame a este método para `CAccessToken` habilitar un privilegio en el objeto.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Llame a este método para habilitar `CAccessToken` uno o varios privilegios en el objeto.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Llame a este `CAccessToken` método para devolver la DACL predeterminada del objeto.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Llame a este `CAccessToken` método para obtener el objeto igual al token de acceso en vigor para el subproceso actual.|
|[CAccessToken::GetGroups](#getgroups)|Llame a este `CAccessToken` método para devolver los grupos de tokens del objeto.|
|[CAccessToken::GetHandle](#gethandle)|Llame a este método para recuperar un identificador para el token de acceso.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Llame a este método para obtener el nivel de suplantación del token de acceso.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Llame a este método para obtener `CAccessToken` el identificador de sesión de inicio de sesión asociado al objeto.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Llame a este método para obtener `CAccessToken` el SID de inicio de sesión asociado al objeto.|
|[CAccessToken::GetOwner](#getowner)|Llame a este método para `CAccessToken` obtener el propietario asociado con el objeto.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Llame a este método para obtener `CAccessToken` el grupo principal asociado con el objeto.|
|[CAccessToken::GetPrivileges](#getprivileges)|Llame a este método para `CAccessToken` obtener los privilegios asociados con el objeto.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.|
|[CAccessToken::GetProfile](#getprofile)|Llame a este método para obtener el identificador `CAccessToken` que apunta al perfil de usuario asociado con el objeto.|
|[CAccessToken::GetSource](#getsource)|Llame a este método para `CAccessToken` obtener el origen del objeto.|
|[CAccessToken::GetStatistics](#getstatistics)|Llame a este método para `CAccessToken` obtener información asociada con el objeto.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Llame a este método para obtener el `CAccessToken` identificador de sesión de Terminal Services asociado al objeto.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Llame a este `CAccessToken` método para inicializar el con el token desde el subproceso especificado.|
|[CAccessToken::GetTokenId](#gettokenid)|Llame a este método para obtener `CAccessToken` el identificador de token asociado al objeto.|
|[CAccessToken::GetType](#gettype)|Llame a este método para `CAccessToken` obtener el tipo de token del objeto.|
|[CAccessToken::GetUser](#getuser)|Llame a este método para `CAccessToken` identificar el usuario asociado con el objeto.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Llame a este método para obtener el identificador `CAccessToken` que apunta al perfil de usuario asociado con el objeto.|
|[CAccessToken::Impersonate](#impersonate)|Llame a este método para `CAccessToken` asignar una suplantación a un subproceso.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Llame a este método para permitir que el subproceso que realiza la llamada suplante el contexto de seguridad de un usuario que ha iniciado sesión.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Llame a este método `CAccessToken` para comprobar si el objeto contiene una lista de SID restringidos.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Llame a este método para cargar `CAccessToken` el perfil de usuario asociado al objeto.|
|[CAccessToken::LogonUser](#logonuser)|Llame a este método para crear una sesión de inicio de sesión para el usuario asociado con las credenciales dadas.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Llame a este método desde un servidor COM que `CAccessToken` controla una llamada desde un cliente para inicializar el con el token de acceso desde el cliente COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Llame a este método desde dentro de un servidor `CAccessToken` que toma solicitudes sobre una canalización con nombre para inicializar el con el token de acceso desde el cliente.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Llame a este método desde dentro de un servidor `CAccessToken` que controla una llamada desde un cliente RPC para inicializar el con el token de acceso desde el cliente.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Llame a este método para establecer el `CAccessToken` nivel de suplantación y, a continuación, inicializar el con el token desde el subproceso especificado.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Llame a este método para determinar si un conjunto `CAccessToken` especificado de privilegios está habilitado en el objeto.|
|[CAccessToken::Revertir](#revert)|Llame a este método para detener un subproceso que usa un token de suplantación.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Llame a este método para establecer `CAccessToken` la DACL predeterminada del objeto.|
|[CAccessToken::SetOwner](#setowner)|Llame a este método para `CAccessToken` establecer el propietario del objeto.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Llame a este método para `CAccessToken` establecer el grupo principal del objeto.|

## <a name="remarks"></a>Observaciones

Un token de [acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

Para obtener una introducción al modelo de control de acceso en Windows, vea Control de [acceso](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::Attach

Llame a este método para tomar posesión del identificador de token de acceso especificado.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parámetros

*hToken*<br/>
Identificador del token de acceso.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se `CAccessToken` producirá un error de aserción si el objeto ya tiene la propiedad de un token de acceso.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken::-CAccessToken

Destructor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Llame a este método para determinar si un `CAccessToken` SID especificado está habilitado en el objeto.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un [CSid Clase](../../atl/reference/csid-class.md) objeto.

*pbIsMember*<br/>
Puntero a una variable que recibe los resultados de la comprobación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El `CheckTokenMembership` método comprueba la presencia del SID en los SID de usuario y grupo del token de acceso. Si el SID está presente y tiene el atributo SE_GROUP_ENABLED, *pbIsMember* se establece en TRUE; de lo contrario, se establece en FALSE.

En compilaciones de depuración, se producirá un error de aserción si *pbIsMember* no es un puntero válido.

> [!NOTE]
> El `CAccessToken` objeto debe ser un token de suplantación y no un token principal.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Llame a este método para crear un token de acceso de suplantación.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Chulo*<br/>
Puntero al `CAccessToken` nuevo objeto.

*Sil*<br/>
Especifica un [tipo enumerado SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) que proporciona el nivel de suplantación del nuevo token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateImpersonationToken`llama a [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) para crear un nuevo token de suplantación.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Llame a este método para crear un nuevo token principal.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPri*<br/>
Puntero al `CAccessToken` nuevo objeto.

*dwDesiredAccess*<br/>
Especifica los derechos de acceso solicitados para el nuevo token. El valor predeterminado, MAXIMUM_ALLOWED, solicita todos los derechos de acceso que son válidos para el autor de la llamada. Consulte [Derechos de acceso y máscaras](/windows/win32/SecAuthZ/access-rights-and-access-masks) de acceso para obtener más información sobre los derechos de acceso.

*pTokenAttributes*<br/>
Puntero a una estructura [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo token y determina si los procesos secundarios pueden heredar el token. Si *pTokenAttributes* es NULL, el token obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreatePrimaryToken`llama a [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) para crear un nuevo token principal.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser

Llame a este método para crear un nuevo proceso que `CAccessToken` se ejecuta en el contexto de seguridad del usuario representado por el objeto.

```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*pApplicationName*<br/>
Puntero a una cadena terminada en null que especifica el módulo que se va a ejecutar. Este parámetro puede no ser NULL.

*pCommandLine*<br/>
Puntero a una cadena terminada en null que especifica la línea de comandos que se va a ejecutar.

*pProcessInformation*<br/>
Puntero a una [estructura de PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) que recibe información de identificación sobre el nuevo proceso.

*pStartupInfo*<br/>
Puntero a una estructura [STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) que especifica cómo debe aparecer la ventana principal para el nuevo proceso.

*dwCreationFlags*<br/>
Especifica indicadores adicionales que controlan la clase de prioridad y la creación del proceso. Consulte la función [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) de Win32 para obtener una lista de indicadores.

*bLoadProfile*<br/>
Si es TRUE, el perfil del usuario se carga con [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Puntero a una estructura [de SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo proceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pProcessAttributes* es NULL, el proceso obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

*pThreadAttributes*<br/>
Puntero a una estructura [de SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo subproceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pThreadAttributes* es NULL, el subproceso obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

*bInherit*<br/>
Indica si el nuevo proceso hereda los identificadores del proceso de llamada. Si TRUE, el nuevo proceso hereda cada identificador abierto heredable en el proceso de llamada. Los identificadores heredados tienen el mismo valor y privilegios de acceso que los identificadores originales.

*pCurrentDirectory*<br/>
Puntero a una cadena terminada en null que especifica la unidad y el directorio actuales para el nuevo proceso. La cadena debe ser una ruta de acceso completa que incluya una letra de unidad. Si este parámetro es NULL, el nuevo proceso tendrá la misma unidad y directorio actuales que el proceso de llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateProcessAsUser`utiliza `CreateProcessAsUser` la función Win32 para crear un nuevo proceso que se `CAccessToken` ejecuta en el contexto de seguridad del usuario representado por el objeto. Consulte la descripción de la función [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) para obtener una explicación completa de los parámetros necesarios.

Para que este método `CAccessToken` se realice correctamente, el objeto debe contener los privilegios AssignPrimaryToken (a menos que sea un token restringido) y Los privilegios IncreaseQuota.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Llame a este método para `CAccessToken` crear un nuevo objeto restringido.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pRestrictedToken*<br/>
El nuevo `CAccessToken` objeto restringido.

*SidsToDisable*<br/>
Objeto `CTokenGroups` que especifica los SID de solo denegación.

*SidsToRestrict*<br/>
Objeto `CTokenGroups` que especifica los SID de restricción.

*PrivilegesToDelete*<br/>
Objeto `CTokenPrivileges` que especifica los privilegios que se deben eliminar en el token restringido. El valor predeterminado crea un objeto vacío.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateRestrictedToken`utiliza la función [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 para crear un nuevo `CAccessToken` objeto, con restricciones.

> [!IMPORTANT]
> Cuando `CreateRestrictedToken`se usa , asegúrese de lo siguiente: el token existente es válido (y no especificado por el usuario) y *SidsToDisable* y *PrivilegesToDelete* son válidos (y no especificados por el usuario). Si el método devuelve FALSE, deniegue la funcionalidad.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

Llame a este método para revocar la propiedad del token de acceso.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador `CAccessToken` al que se ha separado.

### <a name="remarks"></a>Observaciones

Este método revoca `CAccessToken`la propiedad del token de acceso.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege

Llame a este método para `CAccessToken` deshabilitar un privilegio en el objeto.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena que contiene `CAccessToken` el privilegio que se va a deshabilitar en el objeto.

*pPreviousState*<br/>
Puntero a `CTokenPrivileges` un objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::Dprivilegiosables

Llame a este método para deshabilitar `CAccessToken` uno o varios privilegios en el objeto.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
Puntero a una matriz de cadenas que `CAccessToken` contiene los privilegios que se deshabilitarán en el objeto.

*pPreviousState*<br/>
Puntero a `CTokenPrivileges` un objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Llame a este método para `CAccessToken` habilitar un privilegio en el objeto.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena que contiene `CAccessToken` el privilegio que se va a habilitar en el objeto.

*pPreviousState*<br/>
Puntero a `CTokenPrivileges` un objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Llame a este método para habilitar `CAccessToken` uno o varios privilegios en el objeto.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
Puntero a una matriz de cadenas que `CAccessToken` contiene los privilegios que se habilitarán en el objeto.

*pPreviousState*<br/>
Puntero a `CTokenPrivileges` un objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Llame a este `CAccessToken` método para devolver la DACL predeterminada del objeto.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDacl*<br/>
Puntero al objeto [CDacl Class](../../atl/reference/cdacl-class.md) `CAccessToken` que recibirá la DACL predeterminada del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha recuperado la DACL predeterminada, FALSE en caso contrario.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Llame a este `CAccessToken` método para obtener el objeto igual al token de acceso en vigor para el subproceso actual.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::GetGroups

Llame a este `CAccessToken` método para devolver los grupos de tokens del objeto.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pGroups*<br/>
Puntero al objeto [CTokenGroups Clase](../../atl/reference/ctokengroups-class.md) que recibirá la información del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle

Llame a este método para recuperar un identificador para el token de acceso.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador `CAccessToken` al token de acceso del objeto.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Llame a este método para obtener el nivel de suplantación del token de acceso.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pImpersonationLevel*<br/>
Puntero a un tipo de enumeración [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) que recibirá la información de nivel de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Llame a este método para obtener `CAccessToken` el identificador de sesión de inicio de sesión asociado al objeto.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*<br/>
Puntero a un [LUID](/windows/win32/api/winnt/ns-winnt-luid) que recibirá el ID de sesión de inicio de sesión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *pluid* es un valor no válido.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Llame a este método para obtener `CAccessToken` el SID de inicio de sesión asociado al objeto.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid Clase](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si *pSid* es un valor no válido.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::GetOwner

Llame a este método para `CAccessToken` obtener el propietario asociado con el objeto.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid Clase](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El propietario se establece de forma predeterminada en los objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Llame a este método para obtener `CAccessToken` el grupo principal asociado con el objeto.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid Clase](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El grupo se establece de forma predeterminada en los objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Llame a este método para `CAccessToken` obtener los privilegios asociados con el objeto.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*<br/>
Puntero a un [CTokenPrivileges clase](../../atl/reference/ctokenprivileges-class.md) objeto que recibirá los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hProcess*<br/>
Identificador del proceso cuyo token de acceso se abre. Si se utiliza el valor predeterminado de NULL, se utiliza el proceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile

Llame a este método para obtener el identificador `CAccessToken` que apunta al perfil de usuario asociado con el objeto.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource

Llame a este método para `CAccessToken` obtener el origen del objeto.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSource*<br/>
Puntero a una estructura [TOKEN_SOURCE.](/windows/win32/api/winnt/ns-winnt-token_source)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Llame a este método para `CAccessToken` obtener información asociada con el objeto.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pEstadísticas*<br/>
Puntero a una estructura [TOKEN_STATISTICS.](/windows/win32/api/winnt/ns-winnt-token_statistics)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Llame a este método para obtener el `CAccessToken` identificador de sesión de Terminal Services asociado al objeto.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pdwSessionId*<br/>
El ID de sesión de Terminal Services.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Llame a este `CAccessToken` método para inicializar el con el token desde el subproceso especificado.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hThread*<br/>
Controle el subproceso cuyo token de acceso está abierto.

*bOpenAsSelf*<br/>
Indica si se debe realizar la comprobación de acceso en `GetThreadToken` el contexto de seguridad del subproceso que llama al método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Llame a este método para obtener `CAccessToken` el identificador de token asociado al objeto.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*<br/>
Puntero a un [LUID](/windows/win32/api/winnt/ns-winnt-luid) que recibirá el ID de token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType

Llame a este método para `CAccessToken` obtener el tipo de token del objeto.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pType*<br/>
Dirección de la [variable TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) que, en caso de éxito, recibe el tipo del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El tipo de enumeración TOKEN_TYPE contiene valores que diferencian entre un token principal y un token de suplantación.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser

Llame a este método para `CAccessToken` identificar el usuario asociado con el objeto.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*Psid*<br/>
Puntero a un [CSid Clase](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Llame a este método para obtener el identificador `CAccessToken` que apunta al perfil de usuario asociado con el objeto.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Impersonate

Llame a este método para `CAccessToken` asignar una suplantación a un subproceso.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*hThread*<br/>
Controlar el subproceso para asignar el token de suplantación. Este identificador debe haberse abierto con derechos de acceso TOKEN_IMPERSONATE. Si *hThread* es NULL, el método hace que el subproceso deje de usar un token de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si `CAccessToken` no tiene un puntero válido a un token.

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede utilizar para revertir automáticamente los tokens de acceso suplantados.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser

Llame a este método para permitir que el subproceso que realiza la llamada suplante el contexto de seguridad de un usuario que ha iniciado sesión.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

> [!IMPORTANT]
> Si se produce un error en una llamada a una función de suplantación por cualquier motivo, el cliente no se suplanta y la solicitud de cliente se realiza en el contexto de seguridad del proceso desde el que se realizó la llamada. Si el proceso se ejecuta como una cuenta con privilegios elevados o como miembro de un grupo administrativo, es posible que el usuario pueda realizar acciones que de otro modo no se le permitirían. Por lo tanto, el valor devuelto para esta función siempre debe confirmarse.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Llame a este método `CAccessToken` para comprobar si el objeto contiene una lista de SID restringidos.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto contiene una lista de SID de restricción, FALSE si no hay sID de restricción o si se produce un error en el método.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile

Llame a este método para cargar `CAccessToken` el perfil de usuario asociado al objeto.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se `CAccessToken` producirá un error de aserción si no contiene un token válido o si ya existe un perfil de usuario.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUser

Llame a este método para crear una sesión de inicio de sesión para el usuario asociado con las credenciales dadas.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*pszUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre de usuario. Este es el nombre de la cuenta de usuario en la que se va a iniciar sesión.

*pszDomain*<br/>
Puntero a una cadena terminada en null que especifica el nombre del dominio o servidor cuya base de datos de cuentas contiene la cuenta *pszUserName.*

*pszPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña de texto no cifrado para la cuenta de usuario especificada por *pszUserName*.

*dwLogonType*<br/>
Especifica el tipo de operación de inicio de sesión que se va a realizar. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más detalles.

*dwLogonProvider*<br/>
Especifica el proveedor de inicio de sesión. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El token de acceso resultante del `CAccessToken`inicio de sesión se asociará con el archivo . Para que este método `CAccessToken` se realice correctamente, el objeto debe contener privilegios de SE_TCB_NAME, identificando al titular como parte de la base de equipos de confianza. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más información sobre los privilegios necesarios.

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Llame a este método desde un servidor COM que `CAccessToken` controla una llamada desde un cliente para inicializar el con el token de acceso desde el cliente COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso actual suplantará al cliente COM que realiza la llamada si esta llamada se completa correctamente. Si FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si la comprobación de acceso se debe realizar en el contexto de seguridad del subproceso que llama a la [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede utilizar para revertir automáticamente los tokens de acceso suplantados creados estableciendo el indicador *bImpersonate* en TRUE.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Llame a este método desde dentro de un servidor `CAccessToken` que toma solicitudes sobre una canalización con nombre para inicializar el con el token de acceso desde el cliente.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hPipe*<br/>
Manipule a una tubería con nombre.

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso actual suplantará al cliente de canalización que realiza la llamada si esta llamada se completa correctamente. Si FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si la comprobación de acceso se debe realizar en el contexto de seguridad del subproceso que llama a la [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede utilizar para revertir automáticamente los tokens de acceso suplantados creados estableciendo el indicador *bImpersonate* en TRUE.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Llame a este método desde dentro de un servidor `CAccessToken` que controla una llamada desde un cliente RPC para inicializar el con el token de acceso desde el cliente.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*BindingHandle*<br/>
Identificador de enlace en el servidor que representa un enlace a un cliente.

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso actual suplantará al cliente RPC que realiza la llamada si esta llamada se completa correctamente. Si FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si la comprobación de acceso se debe realizar en el contexto de seguridad del subproceso que llama a la [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede utilizar para revertir automáticamente los tokens de acceso suplantados creados estableciendo el indicador *bImpersonate* en TRUE.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken

Llame a este método para establecer el `CAccessToken` nivel de suplantación y, a continuación, inicializar el con el token desde el subproceso especificado.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso se dejará en el nivel de suplantación solicitado después de que se complete este método. Si FALSE, el subproceso volverá a su nivel de suplantación original.

*bOpenAsSelf*<br/>
Indica si la comprobación de acceso se debe realizar en el contexto de seguridad del subproceso que llama a la [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

*Sil*<br/>
Especifica un [tipo enumerado SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) que proporciona el nivel de suplantación del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`OpenThreadToken`es similar a [CAccessToken::GetThreadToken](#getthreadtoken), pero establece el `CAccessToken` nivel de suplantación antes de inicializar el token de acceso del subproceso.

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede utilizar para revertir automáticamente los tokens de acceso suplantados creados estableciendo el indicador *bImpersonate* en TRUE.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck

Llame a este método para determinar si un conjunto `CAccessToken` especificado de privilegios está habilitado en el objeto.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parámetros

*Privilegios requeridos*<br/>
Puntero a una estructura [PRIVILEGE_SET.](/windows/win32/api/winnt/ns-winnt-privilege_set)

*pbResult*<br/>
Puntero a un valor que establece el método para indicar si alguno `CAccessToken` o todos los privilegios especificados están habilitados en el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Cuando `PrivilegeCheck` se `Attributes` devuelve, el miembro de cada [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) estructura se establece en SE_PRIVILEGE_USED_FOR_ACCESS si se habilita el privilegio correspondiente. Este método llama a la función [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Revertir

Llame a este método para impedir que un subproceso use un token de suplantación.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*hThread*<br/>
Controlar el subproceso para revertir de la suplantación. Si *hThread* es NULL, se asume el subproceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La reversión de los tokens de suplantación se puede realizar automáticamente con la [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Llame a este método para establecer `CAccessToken` la DACL predeterminada del objeto.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parámetros

*rDacl*<br/>
La nueva información predeterminada de la [clase CDacl.](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La DACL predeterminada es la DACL que se utiliza de forma predeterminada cuando se crean nuevos objetos con este token de acceso en vigor.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Llame a este método para `CAccessToken` establecer el propietario del objeto.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
El [CSid (clase)](../../atl/reference/csid-class.md) objeto que contiene la información del propietario.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El propietario es el propietario predeterminado que se usa para los nuevos objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Llame a este método para `CAccessToken` establecer el grupo principal del objeto.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
El [cSid clase](../../atl/reference/csid-class.md) objeto que contiene la información del grupo principal.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El grupo principal es el grupo predeterminado para los nuevos objetos creados mientras este token de acceso está en vigor.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokens de acceso](/windows/win32/SecAuthZ/access-tokens)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
