---
title: CAccessToken (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e680bf4c84087db90c794c772f58691a5b2932d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754644"
---
# <a name="caccesstoken-class"></a>CAccessToken (clase)

Esta clase es un contenedor para un token de acceso.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAccessToken
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|Llame a este método para tomar posesión del identificador de token de acceso dada.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Llame a este método para determinar si está habilitado el SID especificado en el `CAccessToken` objeto.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Llame a este método para crear un nuevo token de acceso de suplantación.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Llame a este método para crear un nuevo token principal.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Llame a este método para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Llame a este método para crear un nuevo y restringido `CAccessToken` objeto.|
|[CAccessToken::Detach](#detach)|Llame a este método para revocar la posesión del token de acceso.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Llame a este método para deshabilitar un privilegio en la `CAccessToken` objeto.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Llame a este método para deshabilitar uno o varios privilegios en el `CAccessToken` objeto.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Llame a este método para habilitar un privilegio en la `CAccessToken` objeto.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Llame a este método para habilitar uno o varios privilegios en el `CAccessToken` objeto.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Llame a este método para devolver el `CAccessToken` del objeto predeterminado DACL.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Llame a este método para obtener el `CAccessToken` objeto igual que el token de acceso en vigor para el subproceso actual.|
|[CAccessToken::GetGroups](#getgroups)|Llame a este método para devolver el `CAccessToken` grupos símbolo (token) del objeto.|
|[CAccessToken::GetHandle](#gethandle)|Llame a este método para recuperar un identificador para el token de acceso.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Llame a este método para obtener el nivel de suplantación desde el token de acceso.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Llame a este método para obtener el identificador de sesión de inicio de sesión asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Llame a este método para obtener el SID de inicio de sesión asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetOwner](#getowner)|Llame a este método para obtener el propietario asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Llame a este método para obtener el grupo primario asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetPrivileges](#getprivileges)|Llame a este método para obtener los privilegios asociados con el `CAccessToken` objeto.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.|
|[CAccessToken::GetProfile](#getprofile)|Llame a este método para obtener el identificador que apunta al perfil de usuario asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetSource](#getsource)|Llame a este método para obtener el código fuente de la `CAccessToken` objeto.|
|[CAccessToken::GetStatistics](#getstatistics)|Llame a este método para obtener la información asociada con el `CAccessToken` objeto.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Llame a este método para obtener el identificador de sesión de Terminal Services asociada con el `CAccessToken` objeto.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Llame a este método para inicializar el `CAccessToken` con el token de subproceso dado.|
|[CAccessToken::GetTokenId](#gettokenid)|Llame a este método para obtener el identificador de Token asociado con el `CAccessToken` objeto.|
|[CAccessToken::GetType](#gettype)|Llame a este método para obtener el tipo de token de la `CAccessToken` objeto.|
|[CAccessToken::GetUser](#getuser)|Llame a este método para identificar el usuario asociado con el `CAccessToken` objeto.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Llame a este método para obtener el identificador que apunta al perfil de usuario asociado con el `CAccessToken` objeto.|
|[CAccessToken::Impersonate](#impersonate)|Llame a este método para asignar una suplantación `CAccessToken` a un subproceso.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Llame a este método para permitir que el subproceso de llamada suplantar el contexto de seguridad de un usuario ha iniciado sesión.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Llame a este método para probar si el `CAccessToken` objeto contiene una lista de SID restringidos.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Llamar a este método para cargar el perfil de usuario asociado con el `CAccessToken` objeto.|
|[CAccessToken::LogonUser](#logonuser)|Llame a este método para crear una sesión de inicio de sesión para el usuario asociado con las credenciales proporcionadas.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Llamar a este método desde dentro de un servidor COM que controlar una llamada desde un cliente para inicializar el `CAccessToken` con el token de acceso desde el cliente COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Llame a este método desde dentro de un servidor realizar solicitudes a través de una canalización con nombre para inicializar el `CAccessToken` con el token de acceso del cliente.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Llamar a este método desde un servidor que controla una llamada desde un cliente RPC para inicializar el `CAccessToken` con el token de acceso del cliente.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Llame a este método para establecer el nivel de suplantación y, a continuación, inicialice la `CAccessToken` con el token de subproceso dado.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Llame a este método para determinar si un conjunto especificado de privilegios están habilitadas en el `CAccessToken` objeto.|
|[CAccessToken::Revert](#revert)|Llame a este método para detener un subproceso que está utilizando un token de suplantación.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Llame a este método para establecer el valor predeterminado la DACL de la `CAccessToken` objeto.|
|[CAccessToken::SetOwner](#setowner)|Llame a este método para establecer el propietario de la `CAccessToken` objeto.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Llame a este método para establecer el grupo principal de la `CAccessToken` objeto.|

## <a name="remarks"></a>Comentarios

Un [token de acceso](/windows/desktop/SecAuthZ/access-tokens) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que ha iniciado sesión en un sistema de Windows.

Para obtener una introducción al modelo de control de acceso en Windows, consulte [Control de acceso](/windows/desktop/SecAuthZ/access-control) en el SDK de Windows.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

Llame a este método para tomar posesión del identificador de token de acceso dada.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parámetros

*que hToken*  
Un identificador para el token de acceso.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si el `CAccessToken` objeto ya tiene una propiedad de un token de acceso.

##  <a name="dtor"></a>  CAccessToken:: ~ CAccessToken

Destructor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

Llame a este método para determinar si está habilitado el SID especificado en el `CAccessToken` objeto.

```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*  
Hacer referencia a un [CSid (clase)](../../atl/reference/csid-class.md) objeto.

*pbIsMember*  
Puntero a una variable que recibe los resultados de la comprobación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El `CheckTokenMembership` método comprueba la presencia de SID en el usuario y los SID de grupo del token de acceso. Si el SID está presente y tiene el atributo SE_GROUP_ENABLED, *pbIsMember* está establecido en TRUE; en caso contrario, se establece en FALSE.

En las compilaciones de depuración, se producirá un error de aserción si *pbIsMember* no es un puntero válido.

> [!NOTE]
>  La `CAccessToken` objeto debe ser un token de suplantación y no un token primario.

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

Llame a este método para crear un token de acceso de la suplantación.

```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pImp*  
Puntero a la nueva `CAccessToken` objeto.

*Sil*  
Especifica un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) tipo enumerado que proporciona el nivel de suplantación del token de nuevo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`CreateImpersonationToken` las llamadas [duplicar el elemento](https://msdn.microsoft.com/library/windows/desktop/aa446616) para crear un nuevo token de suplantación.

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

Llame a este método para crear un nuevo token principal.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPri*  
Puntero a la nueva `CAccessToken` objeto.

*dwDesiredAccess*  
Especifica los derechos de acceso solicitado para el nuevo token. El valor predeterminado, MAXIMUM_ALLOWED, solicita todos los derechos de acceso que son válidos para el llamador. Consulte [derechos de acceso y las máscaras de acceso](/windows/desktop/SecAuthZ/access-rights-and-access-masks) para obtener más sobre derechos de acceso.

*pTokenAttributes*  
Puntero a un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo token y determina si los procesos secundarios pueden heredar el token. Si *pTokenAttributes* es NULL, el token Obtiene un descriptor de seguridad predeterminado y no se puede heredar el identificador.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`CreatePrimaryToken` las llamadas [DuplicateTokenEx](https://msdn.microsoft.com/library/windows/desktop/aa446617) para crear un nuevo token principal.

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

Llame a este método para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto.

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

*pApplicationName*  
Puntero a una cadena terminada en null que especifica el módulo se ejecuten. Este parámetro no puede ser NULL.

*pCommandLine*  
Puntero a una cadena terminada en null que especifica la línea de comandos para ejecutar.

*pProcessInformation*  
Puntero a un [PROCESS_INFORMATION](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information) estructura que recibe información de identificación sobre el proceso de nuevo.

*pStartupInfo*  
Puntero a un [STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa) estructura que especifica cómo debe aparecer la ventana principal del nuevo proceso.

*dwCreationFlags*  
Especifica marcas adicionales que controlan la clase de prioridad y la creación del proceso. Vea la función de Win32 [CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429) para obtener una lista de marcas.

*bLoadProfile*  
Si es TRUE, se carga el perfil del usuario con [LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea).

*pProcessAttributes*  
Puntero a un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo proceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pProcessAttributes* es NULL, el proceso obtiene un descriptor de seguridad predeterminado y no se puede heredar el identificador.

*pThreadAttributes*  
Puntero a un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo subproceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pThreadAttributes* es NULL, el subproceso obtiene un descriptor de seguridad predeterminado y no se puede heredar el identificador.

*bInherit*  
Indica si el nuevo proceso hereda controla el proceso de llamada. Si es TRUE, cada identificador abierto heredable en el proceso de llamada se hereda el nuevo proceso. Identificadores heredados tienen los mismos privilegios de acceso y el valor que los identificadores originales.

*pCurrentDirectory*  
Puntero a una cadena terminada en null que especifica la unidad actual y el directorio para el nuevo proceso. La cadena debe ser una ruta de acceso completa que incluye una letra de unidad. Si este parámetro es NULL, el nuevo proceso tendrá la misma unidad actual y el directorio que el proceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`CreateProcessAsUser` usa el `CreateProcessAsUser` función de Win32 para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto. Vea la descripción de la [CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429) función para ver una explicación detallada de los parámetros necesarios.

Para que se realice correctamente, este método la `CAccessToken` debe contener objeto AssignPrimaryToken (a menos que sea un token restringido) y IncreaseQuota privilegios.

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

Llame a este método para crear un nuevo y restringido `CAccessToken` objeto.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pRestrictedToken*  
La nueva restricción `CAccessToken` objeto.

*SidsToDisable*  
Un `CTokenGroups` objeto que especifica el SID de sólo denegación.

*SidsToRestrict*  
Un `CTokenGroups` objeto que especifica el SID restringidos.

*PrivilegesToDelete*  
Un `CTokenPrivileges` objeto que especifica los privilegios que se va a eliminar en el token restringido. El valor predeterminado crea un objeto vacío.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`CreateRestrictedToken` usa el [CreateRestrictedToken](https://msdn.microsoft.com/library/windows/desktop/aa446583) función de Win32 para crear un nuevo `CAccessToken` objeto, con restricciones.

> [!IMPORTANT]
>  Cuando se usa `CreateRestrictedToken`, asegúrese de lo siguiente: el token existente es válido (y no se ha introducido por el usuario) y *SidsToDisable* y *PrivilegesToDelete* son válidas (y no se ha introducido por el usuario). Si el método devuelve FALSE, deniegue la funcionalidad.

##  <a name="detach"></a>  CAccessToken::Detach

Llame a este método para revocar la posesión del token de acceso.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de la `CAccessToken` que se ha desasociado.

### <a name="remarks"></a>Comentarios

Este método se revoca el `CAccessToken`de posesión del token de acceso.

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

Llame a este método para deshabilitar un privilegio en la `CAccessToken` objeto.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*  
Puntero a una cadena que contiene el privilegio para deshabilitar en el `CAccessToken` objeto.

*pPreviousState*  
Puntero a un `CTokenPrivileges` objeto que contiene el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

Llame a este método para deshabilitar uno o varios privilegios en el `CAccessToken` objeto.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*  
Puntero a una matriz de cadenas que contiene los privilegios para deshabilitar en el `CAccessToken` objeto.

*pPreviousState*  
Puntero a un `CTokenPrivileges` objeto que contiene el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

Llame a este método para habilitar un privilegio en la `CAccessToken` objeto.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*pszPrivilege*  
Puntero a una cadena que contiene el privilegio para habilitar en el `CAccessToken` objeto.

*pPreviousState*  
Puntero a un `CTokenPrivileges` objeto que contiene el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

Llame a este método para habilitar uno o varios privilegios en el `CAccessToken` objeto.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parámetros

*rPrivileges*  
Puntero a una matriz de cadenas que contiene los privilegios para habilitar en el `CAccessToken` objeto.

*pPreviousState*  
Puntero a un `CTokenPrivileges` objeto que contiene el estado anterior de los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

Llame a este método para devolver el `CAccessToken` del objeto predeterminado DACL.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pDacl*  
Puntero a la [CDacl (clase)](../../atl/reference/cdacl-class.md) objeto que recibirá la `CAccessToken` del objeto predeterminado DACL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la DACL predeterminada se ha recuperado, FALSE en caso contrario.

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

Llame a este método para obtener el `CAccessToken` objeto igual que el token de acceso en vigor para el subproceso actual.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getgroups"></a>  CAccessToken::GetGroups

Llame a este método para devolver el `CAccessToken` grupos símbolo (token) del objeto.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pGroups*  
Puntero a la [CTokenGroups (clase)](../../atl/reference/ctokengroups-class.md) objeto que recibirá la información del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="gethandle"></a>  CAccessToken::GetHandle

Llame a este método para recuperar un identificador para el token de acceso.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el `CAccessToken` token de acceso del objeto.

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

Llame a este método para obtener el nivel de suplantación desde el token de acceso.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pImpersonationLevel*  
Puntero a un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) tipo de enumeración que recibirá la información de nivel de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

Llame a este método para obtener el identificador de sesión de inicio de sesión asociado con el `CAccessToken` objeto.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*  
Puntero a un [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) que recibirá el identificador de sesión de inicio de sesión.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *pluid* es un valor no válido.

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

Llame a este método para obtener el SID de inicio de sesión asociado con el `CAccessToken` objeto.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*  
Puntero a un [CSid (clase)](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si *pSid* es un valor no válido.

##  <a name="getowner"></a>  CAccessToken::GetOwner

Llame a este método para obtener el propietario asociado con el `CAccessToken` objeto.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*  
Puntero a un [CSid (clase)](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El propietario se establece de forma predeterminada en cualquier objeto creado mientras este token de acceso está en vigor.

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

Llame a este método para obtener el grupo primario asociado con el `CAccessToken` objeto.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*  
Puntero a un [CSid (clase)](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El grupo se establece de forma predeterminada en cualquier objeto creado mientras este token de acceso está en vigor.

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

Llame a este método para obtener los privilegios asociados con el `CAccessToken` objeto.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pPrivileges*  
Puntero a un [CTokenPrivileges (clase)](../../atl/reference/ctokenprivileges-class.md) objeto que recibirá los privilegios.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hProcess*  
Identificador del proceso cuyo token de acceso se abre. Si se usa el valor predeterminado es null, se usa el proceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas del [OpenProcessToken](https://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) función de Win32.

##  <a name="getprofile"></a>  CAccessToken::GetProfile

Llame a este método para obtener el identificador que apunta al perfil de usuario asociado con el `CAccessToken` objeto.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.

##  <a name="getsource"></a>  CAccessToken::GetSource

Llame a este método para obtener el código fuente de la `CAccessToken` objeto.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSource*  
Puntero a un [TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

Llame a este método para obtener la información asociada con el `CAccessToken` objeto.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pStatistics*  
Puntero a un [TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

Llame a este método para obtener el identificador de sesión de Terminal Services asociada con el `CAccessToken` objeto.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pdwSessionId*  
El identificador de sesión de servicios de Terminal Server.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

Llame a este método para inicializar el `CAccessToken` con el token de subproceso dado.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*hThread*  
Identificador del subproceso cuyo token de acceso se abre.

*bOpenAsSelf*  
Indica si la comprobación de acceso es que debe realizarse en el contexto de seguridad de la llamada del subproceso el `GetThreadToken` método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

Llame a este método para obtener el identificador de Token asociado con el `CAccessToken` objeto.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pluid*  
Puntero a un [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) que recibirá el identificador de Token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="gettype"></a>  CAccessToken::GetType

Llame a este método para obtener el tipo de token de la `CAccessToken` objeto.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parámetros

*PEscriba*  
Dirección de la [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type) variable que, si se ejecuta correctamente, recibe el tipo del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El tipo de enumeración TOKEN_TYPE contiene valores que diferencian un token primario y un token de suplantación.

##  <a name="getuser"></a>  CAccessToken::GetUser

Llame a este método para identificar el usuario asociado con el `CAccessToken` objeto.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parámetros

*pSid*  
Puntero a un [CSid (clase)](../../atl/reference/csid-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

Llame a este método para obtener el identificador que apunta al perfil de usuario asociado con el `CAccessToken` objeto.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.

##  <a name="impersonate"></a>  CAccessToken::Impersonate

Llame a este método para asignar una suplantación `CAccessToken` a un subproceso.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parámetros

*hThread*  
Identificador del subproceso para asignar el token de suplantación a. Este identificador debe haberse abierto con derechos de acceso TOKEN_IMPERSONATE. Si *hThread* es NULL, el método hace que el subproceso dejar de usar un token de suplantación.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si `CAccessToken` no tiene un puntero a un token válido.

El [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado.

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

Llame a este método para permitir que el subproceso de llamada suplantar el contexto de seguridad de un usuario ha iniciado sesión.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

> [!IMPORTANT]
>  Si se produce un error en una llamada a una función de la suplantación por cualquier motivo, no se puede suplantar el cliente y se realiza la solicitud de cliente en el contexto de seguridad del proceso desde el que se realizó la llamada. Si el proceso se ejecuta como una cuenta con privilegios elevados o como miembro de un grupo administrativo, el usuario podría ser capaz de realizar las acciones que no estaría en caso contrario permitida. Por lo tanto, siempre se debe confirmar el valor devuelto para esta función.

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

Llame a este método para probar si el `CAccessToken` objeto contiene una lista de SID restringidos.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto contiene una lista de SID, FALSE si no hay ningún SID restringidos, o si se produce un error en el método.

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

Llamar a este método para cargar el perfil de usuario asociado con el `CAccessToken` objeto.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se producirá un error de aserción si el `CAccessToken` no contiene un token válido, o si el perfil de un usuario ya existe.

##  <a name="logonuser"></a>  CAccessToken::LogonUser

Llame a este método para crear una sesión de inicio de sesión para el usuario asociado con las credenciales proporcionadas.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parámetros

*pszUserName*  
Puntero a una cadena terminada en null que especifica el nombre de usuario. Este es el nombre de la cuenta de usuario para iniciar sesión en.

*pszDomain*  
Puntero a una cadena terminada en null que especifica el nombre de dominio o servidor cuya base de datos de cuenta contiene la *pszUserName* cuenta.

*pszPassword*  
Puntero a una cadena terminada en null que especifica la contraseña de texto no cifrado para la cuenta de usuario especificada por *pszUserName*.

*dwLogonType*  
Especifica el tipo de operación de inicio de sesión va a realizar. Consulte [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) para obtener más detalles.

*dwLogonProvider*  
Especifica el proveedor de inicio de sesión. Consulte [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) para obtener más detalles.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El acceso al token resultante desde el inicio de sesión que se asociarán con el `CAccessToken`. Para que se realice correctamente, este método la `CAccessToken` debe contener el objeto privilegios SE_TCB_NAME, que identifica el titular como parte de la base de equipo de confianza. Consulte [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) para obtener más información sobre los privilegios necesarios.

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

Llamar a este método desde dentro de un servidor COM que controlar una llamada desde un cliente para inicializar el `CAccessToken` con el token de acceso desde el cliente COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*  
Si es TRUE, el subproceso actual suplantará al cliente COM que realiza la llamada si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*  
Indica si la comprobación de acceso es que debe realizarse en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado que se creó estableciendo el *bImpersonate* marca en TRUE.

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

Llame a este método desde dentro de un servidor realizar solicitudes a través de una canalización con nombre para inicializar el `CAccessToken` con el token de acceso del cliente.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*hPipe*  
Identificador de una canalización con nombre.

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*  
Si es TRUE, el subproceso actual suplantará al cliente que realiza la llamada de la canalización si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*  
Indica si la comprobación de acceso es que debe realizarse en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado que se creó estableciendo el *bImpersonate* marca en TRUE.

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

Llamar a este método desde un servidor que controla una llamada desde un cliente RPC para inicializar el `CAccessToken` con el token de acceso del cliente.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parámetros

*BindingHandle*  
Identificador de enlace en el servidor que representa un enlace a un cliente.

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*  
Si es TRUE, el subproceso actual suplantará al cliente que realiza la llamada de RPC si esta llamada se completa correctamente. Si es FALSE, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.

*bOpenAsSelf*  
Indica si la comprobación de acceso es que debe realizarse en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado que se creó estableciendo el *bImpersonate* marca en TRUE.

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

Llame a este método para establecer el nivel de suplantación y, a continuación, inicialice la `CAccessToken` con el token de subproceso dado.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parámetros

*dwDesiredAccess*  
Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.

*bImpersonate*  
Si es TRUE, el subproceso se dejarán en el nivel de suplantación solicitado cuando este método finalice. Si es FALSE, el subproceso se restablecerá a su nivel de suplantación original.

*bOpenAsSelf*  
Indica si la comprobación de acceso es que debe realizarse en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.

Si este parámetro es FALSE, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es TRUE, la comprobación de acceso se realiza mediante el contexto de seguridad del proceso para el subproceso que realiza la llamada.

*Sil*  
Especifica un [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) tipo enumerado que proporciona el nivel de suplantación del token.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

`OpenThreadToken` es similar a [CAccessToken::GetThreadToken](#getthreadtoken), pero establece el nivel de suplantación antes de inicializar el `CAccessToken` de token de acceso del subproceso.

El [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado que se creó estableciendo el *bImpersonate* marca en TRUE.

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

Llame a este método para determinar si un conjunto especificado de privilegios están habilitadas en el `CAccessToken` objeto.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```

### <a name="parameters"></a>Parámetros

*RequiredPrivileges*  
Puntero a un [PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set) estructura.

*pbResult*  
Puntero a un valor que el método establece para indicar si se habilitan any o all del privilegio especificado en el `CAccessToken` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Cuando `PrivilegeCheck` que devuelve el `Attributes` miembro de cada [LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes) estructura se establece en SE_PRIVILEGE_USED_FOR_ACCESS si está habilitado el privilegio correspondiente. Este método llama a la [PrivilegeCheck](https://msdn.microsoft.com/library/windows/desktop/aa379304) función de Win32.

##  <a name="revert"></a>  CAccessToken::Revert

Llame a este método para detener un subproceso del uso de un token de suplantación.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*hThread*  
Identificador del subproceso para revertir de suplantación. Si *hThread* es NULL, se supone que el subproceso actual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

La reversión de los tokens de suplantación se puede realizar automáticamente con el [CAutoRevertImpersonation (clase)](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

Llame a este método para establecer el valor predeterminado la DACL de la `CAccessToken` objeto.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parámetros

*rDacl*  
El nuevo valor predeterminado [CDacl (clase)](../../atl/reference/cdacl-class.md) información.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

La DACL predeterminada es la DACL que se usa de forma predeterminada cuando se crean nuevos objetos con este token de acceso en vigor.

##  <a name="setowner"></a>  CAccessToken::SetOwner

Llame a este método para establecer el propietario de la `CAccessToken` objeto.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*  
El [CSid (clase)](../../atl/reference/csid-class.md) que contiene la información del propietario del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El propietario es el propietario predeterminado que se usa para los nuevos objetos que se crearon mientras este token de acceso está en vigor.

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

Llame a este método para establecer el grupo principal de la `CAccessToken` objeto.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parámetros

*rSid*  
El [CSid (clase)](../../atl/reference/csid-class.md) objeto que contiene la información del grupo principal.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

El grupo principal es el grupo predeterminado para nuevos objetos que se crearon mientras este token de acceso está en vigor.

## <a name="see-also"></a>Vea también

[Ejemplo ATLSecurity](../../visual-cpp-samples.md)   
[Tokens de acceso](/windows/desktop/SecAuthZ/access-tokens)   
[Información general de clases](../../atl/atl-class-overview.md)
