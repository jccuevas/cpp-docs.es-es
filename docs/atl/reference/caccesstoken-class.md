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
ms.openlocfilehash: 93e7d6b3bbd26a765e49791a1122cba2a68f6565
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168480"
---
# <a name="caccesstoken-class"></a>Clase CAccessToken

Esta clase es un contenedor para un token de acceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class CAccessToken
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccessToken:: ~ CAccessToken](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccessToken:: Attach](#attach)|Llame a este método para tomar posesión del identificador de token de acceso especificado.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Llame a este método para determinar si un SID especificado está habilitado `CAccessToken` en el objeto.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Llame a este método para crear un nuevo token de acceso de suplantación.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Llame a este método para crear un nuevo token primario.|
|[CAccessToken:: CreateProcessAsUser](#createprocessasuser)|Llame a este método para crear un nuevo proceso que se ejecute en el contexto de seguridad del usuario `CAccessToken` representado por el objeto.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Llame a este método para crear un nuevo objeto `CAccessToken` restringido.|
|[CAccessToken::D Etach](#detach)|Llame a este método para revocar la propiedad del token de acceso.|
|[CAccessToken::D isablePrivilege](#disableprivilege)|Llame a este método para deshabilitar un privilegio `CAccessToken` en el objeto.|
|[CAccessToken::D isablePrivileges](#disableprivileges)|Llame a este método para deshabilitar uno o más privilegios `CAccessToken` en el objeto.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Llame a este método para habilitar un privilegio en `CAccessToken` el objeto.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Llame a este método para habilitar uno o varios privilegios en `CAccessToken` el objeto.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Llame a este método para devolver `CAccessToken` la DACL predeterminada del objeto.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Llame a este método para obtener `CAccessToken` el objeto igual al token de acceso en vigor para el subproceso actual.|
|[CAccessToken:: GetGroups](#getgroups)|Llame a este método para devolver `CAccessToken` los grupos de tokens del objeto.|
|[CAccessToken:: GetHandle](#gethandle)|Llame a este método para recuperar un identificador del token de acceso.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Llame a este método para obtener el nivel de suplantación del token de acceso.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Llame a este método para obtener el identificador de la sesión de `CAccessToken` inicio de sesión asociado al objeto.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Llame a este método para obtener el SID de inicio de `CAccessToken` sesión asociado al objeto.|
|[CAccessToken:: GetOwner](#getowner)|Llame a este método para obtener el propietario asociado al `CAccessToken` objeto.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Llame a este método para obtener el grupo primario asociado al `CAccessToken` objeto.|
|[CAccessToken::GetPrivileges](#getprivileges)|Llame a este método para obtener los privilegios asociados al `CAccessToken` objeto.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.|
|[CAccessToken:: GetProfile](#getprofile)|Llame a este método para obtener el identificador que apunta al perfil de usuario asociado `CAccessToken` al objeto.|
|[CAccessToken:: GetSource](#getsource)|Llame a este método para obtener el origen del `CAccessToken` objeto.|
|[CAccessToken::GetStatistics](#getstatistics)|Llame a este método para obtener información asociada al `CAccessToken` objeto.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Llame a este método para obtener el ID. de sesión de `CAccessToken` Terminal Services asociado al objeto.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Llame a este método para inicializar `CAccessToken` con el token del subproceso especificado.|
|[CAccessToken::GetTokenId](#gettokenid)|Llame a este método para obtener el identificador de token asociado `CAccessToken` al objeto.|
|[CAccessToken:: GetType](#gettype)|Llame a este método para obtener el tipo de token `CAccessToken` del objeto.|
|[CAccessToken:: GetUser](#getuser)|Llame a este método para identificar al usuario asociado al `CAccessToken` objeto.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Llame a este método para obtener el identificador que apunta al perfil de usuario asociado `CAccessToken` al objeto.|
|[CAccessToken:: Impersonate](#impersonate)|Llame a este método para asignar una suplantación `CAccessToken` a un subproceso.|
|[CAccessToken:: ImpersonateLoggedOnUser](#impersonateloggedonuser)|Llame a este método para permitir que el subproceso que realiza la llamada suplante el contexto de seguridad de un usuario que ha iniciado sesión.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Llame a este método para comprobar si `CAccessToken` el objeto contiene una lista de SID restringidos.|
|[CAccessToken:: LoadUserProfile](#loaduserprofile)|Llame a este método para cargar el perfil de usuario asociado `CAccessToken` al objeto.|
|[CAccessToken:: LogonUser](#logonuser)|Llame a este método para crear una sesión de inicio de sesión para el usuario asociado a las credenciales especificadas.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Llame a este método desde un servidor COM que controle una llamada desde un cliente para `CAccessToken` inicializar con el token de acceso desde el cliente com.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Llame a este método desde dentro de un servidor que realiza solicitudes a través de una `CAccessToken` canalización con nombre para inicializar con el token de acceso desde el cliente.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Llame a este método desde un servidor que controle una llamada desde un cliente RPC para `CAccessToken` inicializar con el token de acceso desde el cliente.|
|[CAccessToken:: OpenThreadToken](#openthreadtoken)|Llame a este método para establecer el nivel de suplantación y, `CAccessToken` a continuación, inicialice el con el token del subproceso especificado.|
|[CAccessToken::P rivilegeCheck](#privilegecheck)|Llame a este método para determinar si un conjunto de privilegios especificado está habilitado `CAccessToken` en el objeto.|
|[CAccessToken:: revert](#revert)|Llame a este método para detener un subproceso que está utilizando un token de suplantación.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Llame a este método para establecer la DACL predeterminada del `CAccessToken` objeto.|
|[CAccessToken::SetOwner](#setowner)|Llame a este método para establecer el propietario del `CAccessToken` objeto.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Llame a este método para establecer el grupo primario del `CAccessToken` objeto.|

## <a name="remarks"></a>Observaciones

Un [token de acceso](/windows/win32/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema Windows.

Para obtener una introducción al modelo de control de acceso de Windows, consulte [Access Control](/windows/win32/SecAuthZ/access-control) en el Windows SDK.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken:: Attach

Llame a este método para tomar posesión del identificador de token de acceso especificado.

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parámetros

*hToken*<br/>
Identificador del token de acceso.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si el objeto ya tiene la `CAccessToken` propiedad de un token de acceso.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken:: ~ CAccessToken

Destructor.

```cpp
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Llame a este método para determinar si un SID especificado está habilitado `CAccessToken` en el objeto.

```cpp
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Referencia a un objeto de [clase CSid](../../atl/reference/csid-class.md) .

*pbIsMember*<br/>
Puntero a una variable que recibe los resultados de la comprobación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El `CheckTokenMembership` método comprueba la presencia del SID en los SID de usuario y de grupo del token de acceso. Si el SID está presente y tiene el atributo SE_GROUP_ENABLED, *pbIsMember* se establece en true; de lo contrario, se establece en FALSE.

En las compilaciones de depuración, se producirá un error de aserción si *pbIsMember* no es un puntero válido.

> [!NOTE]
> El `CAccessToken` objeto debe ser un token de suplantación y no un token primario.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Llame a este método para crear un token de acceso de suplantación.

```cpp
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pImp*<br/>
Puntero al nuevo `CAccessToken` objeto.

*SIL*<br/>
Especifica un [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) tipo enumerado que proporciona el nivel de suplantación del nuevo token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateImpersonationToken`llama a [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) para crear un nuevo token de suplantación.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Llame a este método para crear un nuevo token primario.

```cpp
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPri*<br/>
Puntero al nuevo `CAccessToken` objeto.

*dwDesiredAccess*<br/>
Especifica los derechos de acceso solicitados para el nuevo token. El valor predeterminado, MAXIMUM_ALLOWED, solicita todos los derechos de acceso que son válidos para el autor de la llamada. Consulte [derechos de acceso y máscaras de acceso](/windows/win32/SecAuthZ/access-rights-and-access-masks) para obtener más información sobre los derechos de acceso.

*pTokenAttributes*<br/>
Puntero a una estructura de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo token y determina si los procesos secundarios pueden heredar el token. Si *pTokenAttributes* es null, el token obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreatePrimaryToken`llama a [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) para crear un nuevo token primario.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken:: CreateProcessAsUser

Llame a este método para crear un nuevo proceso que se ejecute en el contexto de seguridad del usuario `CAccessToken` representado por el objeto.

```cpp
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
Puntero a una cadena terminada en null que especifica el módulo que se va a ejecutar. Este parámetro no puede ser NULL.

*pCommandLine*<br/>
Puntero a una cadena terminada en null que especifica la línea de comandos que se va a ejecutar.

*pProcessInformation*<br/>
Puntero a una [estructura de PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) que recibe información de identificación sobre el nuevo proceso.

*pStartupInfo*<br/>
Puntero a una estructura [STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) que especifica cómo debe aparecer la ventana principal del nuevo proceso.

*dwCreationFlags*<br/>
Especifica marcas adicionales que controlan la clase de prioridad y la creación del proceso. Vea la función de Win32 [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) para obtener una lista de marcas.

*bLoadProfile*<br/>
Si es TRUE, el perfil del usuario se carga con [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Puntero a una estructura de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo proceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pProcessAttributes* es null, el proceso obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

*pThreadAttributes*<br/>
Puntero a una estructura de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica un descriptor de seguridad para el nuevo subproceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pThreadAttributes* es null, el subproceso obtiene un descriptor de seguridad predeterminado y el identificador no se puede heredar.

*bInherit*<br/>
Indica si el nuevo proceso hereda los identificadores del proceso que realiza la llamada. Si es TRUE, el nuevo proceso hereda cada identificador abierto heredable en el proceso de llamada. Los identificadores heredados tienen el mismo valor y privilegios de acceso que los identificadores originales.

*pCurrentDirectory*<br/>
Puntero a una cadena terminada en null que especifica la unidad y el directorio actuales para el nuevo proceso. La cadena debe ser una ruta de acceso completa que incluya una letra de unidad. Si este parámetro es NULL, el nuevo proceso tendrá la misma unidad actual y el mismo directorio que el proceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateProcessAsUser`utiliza la `CreateProcessAsUser` función de Win32 para crear un nuevo proceso que se ejecute en el contexto de seguridad del usuario representado `CAccessToken` por el objeto. Vea la descripción de la función [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) para obtener una explicación completa de los parámetros necesarios.

Para que este método se ejecute correctamente `CAccessToken` , el objeto debe contener AssignPrimaryToken (a menos que sea un token restringido) y privilegios IncreaseQuota.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Llame a este método para crear un nuevo objeto `CAccessToken` restringido.

```cpp
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pRestrictedToken*<br/>
Nuevo objeto restringido `CAccessToken` .

*SidsToDisable*<br/>
`CTokenGroups` Objeto que especifica los SID de solo denegación.

*SidsToRestrict*<br/>
`CTokenGroups` Objeto que especifica los SID restrictivos.

*PrivilegesToDelete*<br/>
`CTokenPrivileges` Objeto que especifica los privilegios que se van a eliminar en el token restringido. El valor predeterminado crea un objeto vacío.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`CreateRestrictedToken`usa la función [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) de Win32 para crear un `CAccessToken` nuevo objeto, con restricciones.

> [!IMPORTANT]
> Al usar `CreateRestrictedToken`, asegúrese de lo siguiente: el token existente es válido (y no lo especifica el usuario) y *SidsToDisable* y *PrivilegesToDelete* son válidos (y el usuario no los ha escrito). Si el método devuelve FALSE, deniegue la funcionalidad.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::D Etach

Llame a este método para revocar la propiedad del token de acceso.

```cpp
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del `CAccessToken` que se ha desasociado.

### <a name="remarks"></a>Observaciones

Este método revoca la `CAccessToken`propiedad del token de acceso.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::D isablePrivilege

Llame a este método para deshabilitar un privilegio `CAccessToken` en el objeto.

```cpp
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena que contiene el privilegio que se va `CAccessToken` a deshabilitar en el objeto.

*pPreviousState*<br/>
Puntero a un `CTokenPrivileges` objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::D isablePrivileges

Llame a este método para deshabilitar uno o más privilegios `CAccessToken` en el objeto.

```cpp
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
Puntero a una matriz de cadenas que contiene los privilegios que se van `CAccessToken` a deshabilitar en el objeto.

*pPreviousState*<br/>
Puntero a un `CTokenPrivileges` objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Llame a este método para habilitar un privilegio en `CAccessToken` el objeto.

```cpp
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*<br/>
Puntero a una cadena que contiene el privilegio que se va `CAccessToken` a habilitar en el objeto.

*pPreviousState*<br/>
Puntero a un `CTokenPrivileges` objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Llame a este método para habilitar uno o varios privilegios en `CAccessToken` el objeto.

```cpp
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*<br/>
Puntero a una matriz de cadenas que contiene los privilegios que se van `CAccessToken` a habilitar en el objeto.

*pPreviousState*<br/>
Puntero a un `CTokenPrivileges` objeto que contendrá el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Llame a este método para devolver `CAccessToken` la DACL predeterminada del objeto.

```cpp
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDacl*<br/>
Puntero al objeto de la [clase CDacl](../../atl/reference/cdacl-class.md) que recibirá `CAccessToken` la DACL predeterminada del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha recuperado la DACL predeterminada; de lo contrario, devuelve FALSE.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Llame a este método para obtener `CAccessToken` el objeto igual al token de acceso en vigor para el subproceso actual.

```cpp
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken:: GetGroups

Llame a este método para devolver `CAccessToken` los grupos de tokens del objeto.

```cpp
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pGroups*<br/>
Puntero al objeto de la [clase CTokenGroups](../../atl/reference/ctokengroups-class.md) que recibirá la información del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken:: GetHandle

Llame a este método para recuperar un identificador del token de acceso.

```cpp
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador al token `CAccessToken` de acceso del objeto.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Llame a este método para obtener el nivel de suplantación del token de acceso.

```cpp
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pImpersonationLevel*<br/>
Puntero a un tipo de enumeración [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) que recibirá la información del nivel de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Llame a este método para obtener el identificador de la sesión de `CAccessToken` inicio de sesión asociado al objeto.

```cpp
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*<br/>
Puntero a un [LUID](/windows/win32/api/winnt/ns-winnt-luid) que recibirá el identificador de la sesión de inicio de sesión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si *pluid* es un valor no válido.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Llame a este método para obtener el SID de inicio de `CAccessToken` sesión asociado al objeto.

```cpp
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un objeto de [clase CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si *pSid* es un valor no válido.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken:: GetOwner

Llame a este método para obtener el propietario asociado al `CAccessToken` objeto.

```cpp
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un objeto de [clase CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El propietario se establece de forma predeterminada en todos los objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Llame a este método para obtener el grupo primario asociado al `CAccessToken` objeto.

```cpp
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un objeto de [clase CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El grupo se establece de forma predeterminada en todos los objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Llame a este método para obtener los privilegios asociados al `CAccessToken` objeto.

```cpp
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*<br/>
Puntero a un objeto de la [clase CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) que recibirá los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.

```cpp
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hProcess*<br/>
Identificador del proceso cuyo token de acceso se abre. Si se usa el valor predeterminado de NULL, se utiliza el proceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Llama a la función [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) de Win32.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken:: GetProfile

Llame a este método para obtener el identificador que apunta al perfil de usuario asociado `CAccessToken` al objeto.

```cpp
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que señala al perfil de usuario o NULL si no existe ningún perfil.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken:: GetSource

Llame a este método para obtener el origen del `CAccessToken` objeto.

```cpp
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSource*<br/>
Puntero a una estructura de [TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Llame a este método para obtener información asociada al `CAccessToken` objeto.

```cpp
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pStatistics*<br/>
Puntero a una estructura de [TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Llame a este método para obtener el ID. de sesión de `CAccessToken` Terminal Services asociado al objeto.

```cpp
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pdwSessionId*<br/>
IDENTIFICADOR de la sesión de Terminal Services.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Llame a este método para inicializar `CAccessToken` con el token del subproceso especificado.

```cpp
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hThread*<br/>
Identificador del subproceso cuyo token de acceso se abre.

*bOpenAsSelf*<br/>
Indica si se va a realizar la comprobación de acceso en el contexto de seguridad del subproceso `GetThreadToken` que llama al método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza usando el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza usando el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Llame a este método para obtener el identificador de token asociado `CAccessToken` al objeto.

```cpp
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*<br/>
Puntero a un [LUID](/windows/win32/api/winnt/ns-winnt-luid) que recibirá el identificador del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken:: GetType

Llame a este método para obtener el tipo de token `CAccessToken` del objeto.

```cpp
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pType*<br/>
Dirección de la variable de [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) que, si se ejecuta correctamente, recibe el tipo del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El tipo de enumeración TOKEN_TYPE contiene valores que diferencian entre un token primario y un token de suplantación.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken:: GetUser

Llame a este método para identificar al usuario asociado al `CAccessToken` objeto.

```cpp
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*<br/>
Puntero a un objeto de [clase CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Llame a este método para obtener el identificador que apunta al perfil de usuario asociado `CAccessToken` al objeto.

```cpp
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que señala al perfil de usuario o NULL si no existe ningún perfil.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken:: Impersonate

Llame a este método para asignar una suplantación `CAccessToken` a un subproceso.

```cpp
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*hThread*<br/>
Identificador del subproceso al que se va a asignar el token de suplantación. Este identificador debe haberse abierto con derechos de acceso TOKEN_IMPERSONATE. Si *hThread* es null, el método hace que el subproceso deje de usar un token de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se `CAccessToken` producirá un error de aserción si no tiene un puntero válido a un token.

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede usar para revertir automáticamente los tokens de acceso suplantados.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken:: ImpersonateLoggedOnUser

Llame a este método para permitir que el subproceso que realiza la llamada suplante el contexto de seguridad de un usuario que ha iniciado sesión.

```cpp
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

> [!IMPORTANT]
> Si una llamada a una función de suplantación produce un error por alguna razón, el cliente no se suplanta y la solicitud del cliente se realiza en el contexto de seguridad del proceso desde el que se realizó la llamada. Si el proceso se ejecuta como una cuenta con privilegios elevados o como miembro de un grupo administrativo, es posible que el usuario pueda realizar acciones que, de lo contrario, no se permitiría. Por lo tanto, el valor devuelto para esta función siempre debe confirmarse.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Llame a este método para comprobar si `CAccessToken` el objeto contiene una lista de SID restringidos.

```cpp
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto contiene una lista de SID restrictivos, FALSE si no hay SID restrictivos o si se produce un error en el método.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken:: LoadUserProfile

Llame a este método para cargar el perfil de usuario asociado `CAccessToken` al objeto.

```cpp
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si el `CAccessToken` no contiene un token válido o si ya existe un perfil de usuario.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken:: LogonUser

Llame a este método para crear una sesión de inicio de sesión para el usuario asociado a las credenciales especificadas.

```cpp
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*pszUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre de usuario. Es el nombre de la cuenta de usuario en la que se va a iniciar sesión.

*pszDomain*<br/>
Puntero a una cadena terminada en null que especifica el nombre del dominio o servidor cuya base de datos de cuenta contiene la cuenta *pszUserName* .

*pszPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña de texto no cifrado para la cuenta de usuario especificada por *pszUserName*.

*dwLogonType*<br/>
Especifica el tipo de operación de inicio de sesión que se va a realizar. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más detalles.

*dwLogonProvider*<br/>
Especifica el proveedor de inicio de sesión. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El token de acceso resultante del inicio de sesión se asociará `CAccessToken`a. Para que este método se ejecute correctamente `CAccessToken` , el objeto debe tener privilegios de SE_TCB_NAME, lo que identifica al titular como parte de la base del equipo de confianza. Consulte [LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) para obtener más información sobre los privilegios necesarios.

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Llame a este método desde un servidor COM que controle una llamada desde un cliente para `CAccessToken` inicializar con el token de acceso desde el cliente com.

```cpp
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso actual suplantará al cliente COM que realiza la llamada si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si se va a realizar la comprobación de acceso en el contexto de seguridad del subproceso que llama al método [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza usando el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza usando el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede usar para revertir automáticamente los tokens de acceso suplantados creados estableciendo la marca *bImpersonate* en true.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Llame a este método desde dentro de un servidor que realiza solicitudes a través de una `CAccessToken` canalización con nombre para inicializar con el token de acceso desde el cliente.

```cpp
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hPipe*<br/>
Identificador de una canalización con nombre.

*dwDesiredAccess*<br/>
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*<br/>
Si es TRUE, el subproceso actual suplantará al cliente de canalización de llamada si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si se va a realizar la comprobación de acceso en el contexto de seguridad del subproceso que llama al método [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza usando el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza usando el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede usar para revertir automáticamente los tokens de acceso suplantados creados estableciendo la marca *bImpersonate* en true.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Llame a este método desde un servidor que controle una llamada desde un cliente RPC para `CAccessToken` inicializar con el token de acceso desde el cliente.

```cpp
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
Si es TRUE, el subproceso actual suplantará al cliente RPC que realiza la llamada si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*<br/>
Indica si se va a realizar la comprobación de acceso en el contexto de seguridad del subproceso que llama al método [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza usando el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza usando el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede usar para revertir automáticamente los tokens de acceso suplantados creados estableciendo la marca *bImpersonate* en true.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken:: OpenThreadToken

Llame a este método para establecer el nivel de suplantación y, `CAccessToken` a continuación, inicialice el con el token del subproceso especificado.

```cpp
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
Si es TRUE, el subproceso se dejará en el nivel de suplantación solicitado una vez completado este método. Si es FALSE, el subproceso revertirá a su nivel de suplantación original.

*bOpenAsSelf*<br/>
Indica si se va a realizar la comprobación de acceso en el contexto de seguridad del subproceso que llama al método [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza usando el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser el de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza usando el contexto de seguridad del proceso para el subproceso que realiza la llamada.

*SIL*<br/>
Especifica un [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) tipo enumerado que proporciona el nivel de suplantación del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

`OpenThreadToken`es similar a [CAccessToken:: GetThreadToken](#getthreadtoken), pero establece el nivel `CAccessToken` de suplantación antes de inicializar desde el token de acceso del subproceso.

La [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se puede usar para revertir automáticamente los tokens de acceso suplantados creados estableciendo la marca *bImpersonate* en true.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::P rivilegeCheck

Llame a este método para determinar si un conjunto de privilegios especificado está habilitado `CAccessToken` en el objeto.

```cpp
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parámetros

*RequiredPrivileges*<br/>
Puntero a una estructura de [PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) .

*pbResult*<br/>
Puntero a un valor que el método establece para indicar si alguno o todos los privilegios especificados están habilitados `CAccessToken` en el objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Cuando `PrivilegeCheck` devuelve, el `Attributes` miembro de cada estructura de [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) se establece en SE_PRIVILEGE_USED_FOR_ACCESS si el privilegio correspondiente está habilitado. Este método llama a la función [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) de Win32.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken:: revert

Llame a este método para impedir que un subproceso use un token de suplantación.

```cpp
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*hThread*<br/>
Identificador del subproceso que se va a revertir de la suplantación. Si *hThread* es null, se supone que es el subproceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La reversión de los tokens de suplantación se puede realizar automáticamente con la [clase CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Llame a este método para establecer la DACL predeterminada del `CAccessToken` objeto.

```cpp
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parámetros

*rDacl*<br/>
La nueva información predeterminada de la [clase CDacl](../../atl/reference/cdacl-class.md) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

La DACL predeterminada es la DACL que se utiliza de forma predeterminada cuando se crean nuevos objetos con este token de acceso en vigor.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Llame a este método para establecer el propietario del `CAccessToken` objeto.

```cpp
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto de la [clase CSid](../../atl/reference/csid-class.md) que contiene la información de propietario.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El propietario es el propietario predeterminado que se usa para los nuevos objetos creados mientras este token de acceso está en vigor.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Llame a este método para establecer el grupo primario del `CAccessToken` objeto.

```cpp
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*<br/>
Objeto de la [clase CSid](../../atl/reference/csid-class.md) que contiene la información del grupo principal.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

El grupo principal es el grupo predeterminado para los nuevos objetos creados mientras este token de acceso está en vigor.

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokens de acceso](/windows/win32/SecAuthZ/access-tokens)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
