---
title: Clase CAccessToken | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3df4c5ac46c159cd3ed955621af914c677182a57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="caccesstoken-class"></a>Clase CAccessToken
Esta clase es un contenedor para un token de acceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAccessToken
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccessToken:: ~ CAccessToken](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccessToken::Attach](#attach)|Llame a este método para tomar posesión del identificador de token de acceso determinada.|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Llamar a este método para determinar si está habilitado un SID especificado en el `CAccessToken` objeto.|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Llame a este método para crear un nuevo token de acceso de suplantación.|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Llame a este método para crear un nuevo token principal.|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Llamar a este método para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto.|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Llamar a este método para crear un nuevo y restringido `CAccessToken` objeto.|  
|[CAccessToken::Detach](#detach)|Llamar a este método para revocar la posesión del token de acceso.|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|Llamar a este método para deshabilitar un privilegio en la `CAccessToken` objeto.|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|Llamar a este método para deshabilitar los privilegios de uno o varios de los `CAccessToken` objeto.|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|Llamar a este método para habilitar un privilegio en la `CAccessToken` objeto.|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|Llamar a este método para habilitar uno o más privilegios en el `CAccessToken` objeto.|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Llamar a este método para devolver el `CAccessToken` del objeto predeterminado DACL.|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Llamar a este método para obtener la `CAccessToken` objeto igual que el token de acceso en vigor para el subproceso actual.|  
|[CAccessToken::GetGroups](#getgroups)|Llamar a este método para devolver el `CAccessToken` grupos de símbolo (token) del objeto.|  
|[CAccessToken::GetHandle](#gethandle)|Llamar a este método para recuperar un identificador para el token de acceso.|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Llamar a este método para obtener el nivel de suplantación desde el token de acceso.|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Llamar a este método para obtener el identificador de sesión de inicio de sesión asociado a la `CAccessToken` objeto.|  
|[CAccessToken::GetLogonSid](#getlogonsid)|Llamar a este método para obtener el SID de inicio de sesión asociado a la `CAccessToken` objeto.|  
|[CAccessToken::GetOwner](#getowner)|Llamar a este método para obtener el propietario asociado con el `CAccessToken` objeto.|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Llamar a este método para obtener el grupo primario asociado con el `CAccessToken` objeto.|  
|[CAccessToken::GetPrivileges](#getprivileges)|Llamar a este método para obtener los privilegios asociados con el `CAccessToken` objeto.|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.|  
|[CAccessToken::GetProfile](#getprofile)|Llamar a este método para obtener el identificador que apunta al perfil de usuario asociado a la `CAccessToken` objeto.|  
|[CAccessToken::GetSource](#getsource)|Llamar a este método para obtener el origen de la `CAccessToken` objeto.|  
|[CAccessToken::GetStatistics](#getstatistics)|Llamar a este método para obtener la información asociada con el `CAccessToken` objeto.|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Llamar a este método para obtener el identificador de sesión de Terminal Services asociada a la `CAccessToken` objeto.|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|Llamar a este método para inicializar el `CAccessToken` con el token del subproceso especificado.|  
|[CAccessToken::GetTokenId](#gettokenid)|Llamar a este método para obtener el identificador del Token asociado a la `CAccessToken` objeto.|  
|[CAccessToken::GetType](#gettype)|Llamar a este método para obtener el tipo de token de la `CAccessToken` objeto.|  
|[CAccessToken::GetUser](#getuser)|Llamar a este método para identificar el usuario asociado a la `CAccessToken` objeto.|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Llamar a este método para obtener el identificador que apunta al perfil de usuario asociado a la `CAccessToken` objeto.|  
|[CAccessToken::Impersonate](#impersonate)|Llamar a este método para asignar una suplantación `CAccessToken` a un subproceso.|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Llamar a este método para permitir que el subproceso que realiza la llamada suplantar el contexto de seguridad de un usuario ha iniciado sesión.|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Llamar a este método para comprobar si la `CAccessToken` objeto contiene una lista de SID restringido.|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Llamar a este método para cargar el perfil de usuario asociado a la `CAccessToken` objeto.|  
|[CAccessToken::LogonUser](#logonuser)|Llame a este método para crear un inicio de sesión para el usuario asociado a las credenciales proporcionadas.|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Llamar a este método desde dentro de un servidor COM que controlar una llamada desde un cliente para inicializar el `CAccessToken` con el token de acceso desde el cliente COM.|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Llamar a este método desde dentro de un servidor realizar solicitudes a través de una canalización con nombre para inicializar el `CAccessToken` con el token de acceso del cliente.|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Llamar a este método desde un servidor de control de una llamada desde un cliente RPC para inicializar el `CAccessToken` con el token de acceso del cliente.|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Llamar a este método para establecer el nivel de suplantación y, a continuación, inicializar el `CAccessToken` con el token del subproceso especificado.|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Llamar a este método para determinar si se habilita un conjunto especificado de privilegios en el **CAccessToken** objeto.|  
|[CAccessToken::Revert](#revert)|Llamar a este método para detener un subproceso que está utilizando un token de suplantación.|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Llamar a este método para establecer el valor predeterminado DACL de la `CAccessToken` objeto.|  
|[CAccessToken::SetOwner](#setowner)|Llamar a este método para establecer el propietario de la `CAccessToken` objeto.|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Llamar a este método para establecer el grupo primario de la `CAccessToken` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Un [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o subproceso y se asigna a cada usuario que haya iniciado sesión en un sistema de Windows NT o Windows 2000.  
  
 Para obtener una introducción al modelo de control de acceso en Windows, consulte [el Control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en el SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h  
  
##  <a name="attach"></a>CAccessToken::Attach  
 Llame a este método para tomar posesión del identificador de token de acceso determinada.  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *que hToken*  
 Un identificador para el token de acceso.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si el `CAccessToken` objeto ya tiene una propiedad de un token de acceso.  
  
##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken  
 Destructor.  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership  
 Llamar a este método para determinar si está habilitado un SID especificado en el `CAccessToken` objeto.  
  
```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 Referencia a un [CSid clase](../../atl/reference/csid-class.md) objeto.  
  
 `pbIsMember`  
 Puntero a una variable que recibe los resultados de la comprobación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El `CheckTokenMembership` método comprueba la presencia del SID en el usuario y el SID de grupo del token de acceso. Si el SID está presente y tiene el atributo SE_GROUP_ENABLED, *pbIsMember* está establecido en true; en caso contrario, se establece en false.  
  
 En las compilaciones de depuración, se producirá un error de aserción si `pbIsMember` no es un puntero válido.  
  
> [!NOTE]
>  La `CAccessToken` objeto debe ser un token de suplantación y no un token primario.  
  
##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken  
 Llame a este método para crear un token de acceso de suplantación.  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pImp`  
 Puntero a la nueva `CAccessToken` objeto.  
  
 `sil`  
 Especifica un [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) tipo enumerado que proporciona el nivel de suplantación del token de nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 `CreateImpersonationToken`llamadas [duplicar el elemento](http://msdn.microsoft.com/library/windows/desktop/aa446616) para crear un nuevo token de suplantación.  
  
##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken  
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
  
 `dwDesiredAccess`  
 Especifica los derechos de acceso solicitado para el nuevo token. El valor predeterminado, MAXIMUM_ALLOWED, solicita todos los derechos de acceso que son válidos para el llamador. Vea [derechos de acceso y las máscaras de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374902) para más de derechos de acceso.  
  
 *pTokenAttributes*  
 Puntero a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo token y determina si los procesos secundarios pueden heredar el token. Si *pTokenAttributes* es NULL, el token Obtiene un descriptor de seguridad predeterminado y el identificador no puede heredarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 `CreatePrimaryToken`llamadas [DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617) para crear un nuevo token principal.  
  
##  <a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser  
 Llamar a este método para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto.  
  
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
 Puntero a un [PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873) estructura que recibe información de identificación sobre el proceso de nuevo.  
  
 *pStartupInfo*  
 Puntero a un [STARTUPINFO](http://msdn.microsoft.com/library/windows/desktop/ms686331) estructura que especifica cómo debe aparecer la ventana principal para el nuevo proceso.  
  
 `dwCreationFlags`  
 Especifica las marcas adicionales que controlan la clase de prioridad y la creación del proceso. Vea la función de Win32 [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) para obtener una lista de marcas.  
  
 *bLoadProfile*  
 Si es true, el perfil del usuario se carga con [LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281).  
  
 *pProcessAttributes*  
 Puntero a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo proceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pProcessAttributes* es NULL, el proceso obtiene un descriptor de seguridad predeterminado y el identificador no puede heredarse.  
  
 *pThreadAttributes*  
 Puntero a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica un descriptor de seguridad para el nuevo subproceso y determina si los procesos secundarios pueden heredar el identificador devuelto. Si *pThreadAttributes* es NULL, el subproceso obtiene un descriptor de seguridad predeterminado y el identificador no puede heredarse.  
  
 *bInherit*  
 Indica si el nuevo proceso hereda identificadores del proceso que realiza la llamada. Si es true, cada identificador heredable abierto en el proceso de llamada es heredado por el nuevo proceso. Identificadores heredados tienen los mismos privilegios de acceso y valor que los identificadores originales.  
  
 *pCurrentDirectory*  
 Puntero a una cadena terminada en null que especifica la unidad actual y el directorio para el nuevo proceso. La cadena debe ser una ruta de acceso completa que incluya una letra de unidad. Si este parámetro es NULL, el nuevo proceso tendrá la misma unidad y directorio actuales que el proceso que realiza la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 **CreateProcessAsUser** utiliza la `CreateProcessAsUser` función de Win32 para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por la `CAccessToken` objeto. Vea la descripción de la [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) función para obtener una explicación completa de los parámetros necesarios.  
  
 Para que se realiza correctamente, este método la `CAccessToken` objeto debe contener AssignPrimaryToken (a menos que sea un token restringido) y privilegios de IncreaseQuota.  
  
##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken  
 Llamar a este método para crear un nuevo y restringido `CAccessToken` objeto.  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pRestrictedToken*  
 Restringe la nueva `CAccessToken` objeto.  
  
 `SidsToDisable`  
 Un `CTokenGroups` objeto que especifica los SID de sólo denegación.  
  
 *SidsToRestrict*  
 Un `CTokenGroups` objeto que especifica los SID que restringen.  
  
 `PrivilegesToDelete`  
 Un `CTokenPrivileges` objeto que especifica los privilegios para eliminar en el token restringido. El valor predeterminado crea un objeto vacío.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 `CreateRestrictedToken`usa el [CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583) función de Win32 para crear un nuevo `CAccessToken` objeto, con restricciones.  
  
> [!NOTE]
>  Este método solo está disponible en Windows 2000 o posterior.  
  
> [!IMPORTANT]
>  Cuando se usa `CreateRestrictedToken`, asegúrese de lo siguiente: el token existente es válida (y no se ha introducido por el usuario) y `SidsToDisable` y `PrivilegesToDelete` son válidas (y no se ha introducido por el usuario). Si el método devuelve false, denegar funcionalidad.  
  
##  <a name="detach"></a>CAccessToken::Detach  
 Llamar a este método para revocar la posesión del token de acceso.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador para el `CAccessToken` que se ha desasociado.  
  
### <a name="remarks"></a>Comentarios  
 Este método se revoca el `CAccessToken`de posesión del token de acceso.  
  
##  <a name="disableprivilege"></a>CAccessToken::DisablePrivilege  
 Llamar a este método para deshabilitar un privilegio en la `CAccessToken` objeto.  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrivilege`  
 Puntero a una cadena que contiene el privilegio para deshabilitar en el `CAccessToken` objeto.  
  
 `pPreviousState`  
 Puntero a un `CTokenPrivileges` objeto que va a contener el estado anterior de los privilegios.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="disableprivileges"></a>CAccessToken::DisablePrivileges  
 Llamar a este método para deshabilitar los privilegios de uno o varios de los `CAccessToken` objeto.  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rPrivileges`  
 Puntero a una matriz de cadenas que contienen los privilegios para deshabilitar en el `CAccessToken` objeto.  
  
 `pPreviousState`  
 Puntero a un `CTokenPrivileges` objeto que va a contener el estado anterior de los privilegios.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege  
 Llamar a este método para habilitar un privilegio en la `CAccessToken` objeto.  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszPrivilege`  
 Puntero a una cadena que contiene el privilegio para permitir la `CAccessToken` objeto.  
  
 `pPreviousState`  
 Puntero a un `CTokenPrivileges` objeto que va a contener el estado anterior de los privilegios.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges  
 Llamar a este método para habilitar uno o más privilegios en el `CAccessToken` objeto.  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rPrivileges`  
 Puntero a una matriz de cadenas que contienen los privilegios para permitir la `CAccessToken` objeto.  
  
 `pPreviousState`  
 Puntero a un `CTokenPrivileges` objeto que va a contener el estado anterior de los privilegios.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl  
 Llamar a este método para devolver el `CAccessToken` del objeto predeterminado DACL.  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDacl`  
 Puntero a la [CDacl clase](../../atl/reference/cdacl-class.md) objeto que va a recibir el **CAccessToken** del objeto predeterminado DACL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la DACL predeterminada ha recuperado.  
  
##  <a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken  
 Llamar a este método para obtener la `CAccessToken` objeto igual que el token de acceso en vigor para el subproceso actual.  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getgroups"></a>CAccessToken::GetGroups  
 Llamar a este método para devolver el `CAccessToken` grupos de símbolo (token) del objeto.  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pGroups*  
 Puntero a la [CTokenGroups clase](../../atl/reference/ctokengroups-class.md) objeto que recibirá la información del grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="gethandle"></a>CAccessToken::GetHandle  
 Llamar a este método para recuperar un identificador para el token de acceso.  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador para el `CAccessToken` token de acceso del objeto.  
  
##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel  
 Llamar a este método para obtener el nivel de suplantación desde el token de acceso.  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pImpersonationLevel*  
 Puntero a un [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) tipo de enumeración que recibirá la información de nivel de suplantación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId  
 Llamar a este método para obtener el identificador de sesión de inicio de sesión asociado a la `CAccessToken` objeto.  
  
```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pluid`  
 Puntero a un [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) que va a recibir el identificador de sesión de inicio de sesión.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si `pluid` es un valor no válido.  
  
##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid  
 Llamar a este método para obtener el SID de inicio de sesión asociado a la `CAccessToken` objeto.  
  
```
bool GetLogonSid(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid clase](../../atl/reference/csid-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si *pSid* es un valor no válido.  
  
##  <a name="getowner"></a>CAccessToken::GetOwner  
 Llamar a este método para obtener el propietario asociado con el `CAccessToken` objeto.  
  
```
bool GetOwner(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid clase](../../atl/reference/csid-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El propietario se establece de forma predeterminada en cualquier objeto creado mientras este token de acceso está en vigor.  
  
##  <a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup  
 Llamar a este método para obtener el grupo primario asociado con el `CAccessToken` objeto.  
  
```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid clase](../../atl/reference/csid-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El grupo se establece de forma predeterminada en cualquier objeto creado mientras este token de acceso está en vigor.  
  
##  <a name="getprivileges"></a>CAccessToken::GetPrivileges  
 Llamar a este método para obtener los privilegios asociados con el `CAccessToken` objeto.  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pPrivileges`  
 Puntero a un [CTokenPrivileges clase](../../atl/reference/ctokenprivileges-class.md) objeto que recibirá los privilegios.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken  
 Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.  
  
```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 *hProcess*  
 Identificador del proceso cuyo token de acceso se abre. Si se usa el valor predeterminado `NULL`, se utilizará el proceso actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `true` si la operación se realiza correctamente; de lo contrario, devuelve `false`.  
  
### <a name="remarks"></a>Comentarios  
 Llamadas a la [OpenProcessToken](http://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) función de Win32.  
  
##  <a name="getprofile"></a>CAccessToken::GetProfile  
 Llamar a este método para obtener el identificador que apunta al perfil de usuario asociado a la `CAccessToken` objeto.  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.  
  
##  <a name="getsource"></a>CAccessToken::GetSource  
 Llamar a este método para obtener el origen de la `CAccessToken` objeto.  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pSource*  
 Puntero a un [TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getstatistics"></a>CAccessToken::GetStatistics  
 Llamar a este método para obtener la información asociada con el `CAccessToken` objeto.  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pStatistics*  
 Puntero a un [TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId  
 Llamar a este método para obtener el identificador de sesión de Terminal Services asociada a la `CAccessToken` objeto.  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 *pdwSessionId*  
 El identificador de sesión de servicios de Terminal Server.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken  
 Llamar a este método para inicializar el `CAccessToken` con el token del subproceso especificado.  
  
```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 `hThread`  
 Identificador del subproceso cuyo token de acceso está abierto.  
  
 `bOpenAsSelf`  
 Indica si la comprobación de acceso se realiza en el contexto de seguridad de la llamada del subproceso del `GetThreadToken` método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 Si este parámetro es false, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es true, la comprobación de acceso se realiza utilizando el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="gettokenid"></a>CAccessToken::GetTokenId  
 Llamar a este método para obtener el identificador del Token asociado a la `CAccessToken` objeto.  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pluid`  
 Puntero a un [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) que va a recibir el identificador de Token.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="gettype"></a>CAccessToken::GetType  
 Llamar a este método para obtener el tipo de token de la `CAccessToken` objeto.  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pType`  
 Dirección de la [TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633) variable que se ejecuta correctamente, recibe el tipo del token.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El **TOKEN_TYPE** tipo de enumeración contiene valores que diferencian entre un token primario y un token de suplantación.  
  
##  <a name="getuser"></a>CAccessToken::GetUser  
 Llamar a este método para identificar el usuario asociado a la `CAccessToken` objeto.  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSid`  
 Puntero a un [CSid clase](../../atl/reference/csid-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser  
 Llamar a este método para obtener el identificador que apunta al perfil de usuario asociado a la `CAccessToken` objeto.  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador que apunta al perfil de usuario, o NULL si no existe ningún perfil.  
  
##  <a name="impersonate"></a>CAccessToken::Impersonate  
 Llamar a este método para asignar una suplantación `CAccessToken` a un subproceso.  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `hThread`  
 Identificador para el subproceso para asignar el token de suplantación. Este identificador debe haberse abierto con derechos de acceso TOKEN_IMPERSONATE. Si `hThread` es NULL, el método hace que el subproceso dejar de usar un token de suplantación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si `CAccessToken` no tiene un puntero a un token válido.  
  
 El [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado.  
  
##  <a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser  
 Llamar a este método para permitir que el subproceso que realiza la llamada suplantar el contexto de seguridad de un usuario ha iniciado sesión.  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
  
> [!IMPORTANT]
>  Si se produce un error en una llamada a una función de suplantación por cualquier motivo, no se suplanta al cliente y la solicitud de cliente se realiza en el contexto de seguridad del proceso desde el que se realizó la llamada. Si el proceso se ejecuta como una cuenta con privilegios elevados, o como un miembro de un grupo administrativo, el usuario podría ser capaz de realizar acciones que circunstancias en caso contrario, no está permitido. Por lo tanto, siempre se debe confirmar el valor devuelto por esta función.  
  
##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted  
 Llamar a este método para comprobar si la `CAccessToken` objeto contiene una lista de SID restringido.  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el objeto contiene una lista de los SID, false si no hay ningún SID de restricción o si se produce un error en el método.  
  
##  <a name="loaduserprofile"></a>CAccessToken::LoadUserProfile  
 Llamar a este método para cargar el perfil de usuario asociado a la `CAccessToken` objeto.  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si el `CAccessToken` no contiene un token válido, o si un usuario de perfil ya existe.  
  
##  <a name="logonuser"></a>CAccessToken::LogonUser  
 Llame a este método para crear un inicio de sesión para el usuario asociado a las credenciales proporcionadas.  
  
```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pszUserName`  
 Puntero a una cadena terminada en null que especifica el nombre de usuario. Este es el nombre de la cuenta de usuario para iniciar una sesión.  
  
 *pszDomain*  
 Puntero a una cadena terminada en null que especifica el nombre del dominio o del servidor cuya base de datos de cuenta contiene la `pszUserName` cuenta.  
  
 `pszPassword`  
 Puntero a una cadena terminada en null que especifica la contraseña de texto no cifrado para la cuenta de usuario especificada por `pszUserName`.  
  
 *dwLogonType*  
 Especifica el tipo de operación de inicio de sesión que se realiza. Vea [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) para obtener más detalles.  
  
 *dwLogonProvider*  
 Especifica el proveedor de inicio de sesión. Vea [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El acceso de token resultante desde el inicio de sesión se asociará con la `CAccessToken`. Para que este método se realiza correctamente, el `CAccessToken` debe contener el objeto privilegios SE_TCB_NAME, identifica el titular como parte de la base de equipo de confianza. Vea [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) para obtener más información sobre los privilegios necesarios.  
  
##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken  
 Llamar a este método desde dentro de un servidor COM que controlar una llamada desde un cliente para inicializar el `CAccessToken` con el token de acceso desde el cliente COM.  
  
```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 `bImpersonate`  
 Si es true, el subproceso actual suplantará al cliente COM que realiza la llamada si esta llamada se completa correctamente. Si es false, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.  
  
 `bOpenAsSelf`  
 Indica si la comprobación de acceso se realiza en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 Si este parámetro es false, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es true, la comprobación de acceso se realiza utilizando el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado creados estableciendo la `bImpersonate` indicador en *true*.  
  
##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken  
 Llamar a este método desde dentro de un servidor realizar solicitudes a través de una canalización con nombre para inicializar el `CAccessToken` con el token de acceso del cliente.  
  
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
  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 `bImpersonate`  
 Si es true, el subproceso actual suplantará al cliente que realiza la llamada de la canalización si esta llamada se completa correctamente. Si es false, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.  
  
 `bOpenAsSelf`  
 Indica si la comprobación de acceso se realiza en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 Si este parámetro es false, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es true, la comprobación de acceso se realiza utilizando el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado creados estableciendo la `bImpersonate` indicador en *true*.  
  
##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken  
 Llamar a este método desde un servidor de control de una llamada desde un cliente RPC para inicializar el `CAccessToken` con el token de acceso del cliente.  
  
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
  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 `bImpersonate`  
 Si es true, el subproceso actual suplantará al cliente que realiza la llamada de RPC si esta llamada se completa correctamente. Si es false, se abrirá el token de acceso, pero el subproceso no tendrá un token de suplantación cuando se complete esta llamada.  
  
 `bOpenAsSelf`  
 Indica si la comprobación de acceso se realiza en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 Si este parámetro es false, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es true, la comprobación de acceso se realiza utilizando el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado creados estableciendo la `bImpersonate` indicador en *true*.  
  
##  <a name="openthreadtoken"></a>CAccessToken::OpenThreadToken  
 Llamar a este método para establecer el nivel de suplantación y, a continuación, inicializar el `CAccessToken` con el token del subproceso especificado.  
  
```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDesiredAccess`  
 Establece una máscara de acceso que especifica los tipos de acceso solicitados para el token de acceso. Estos tipos de acceso solicitados se comparan con una DACL del token para determinar los accesos que se conceden o se deniegan.  
  
 `bImpersonate`  
 Si es true, el subproceso quedará en el nivel de suplantación solicitado cuando este método finalice. Si es false, el subproceso se restablecerá a su nivel de suplantación original.  
  
 `bOpenAsSelf`  
 Indica si la comprobación de acceso se realiza en el contexto de seguridad de la llamada del subproceso del [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) método o en el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 Si este parámetro es false, la comprobación de acceso se realiza mediante el contexto de seguridad para el subproceso que realiza la llamada. Si el subproceso está suplantando a un cliente, este contexto de seguridad puede ser de un proceso de cliente. Si este parámetro es true, la comprobación de acceso se realiza utilizando el contexto de seguridad del proceso para el subproceso que realiza la llamada.  
  
 `sil`  
 Especifica un [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) tipo enumerado que proporciona el nivel de suplantación del token.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 `OpenThreadToken`es similar a [CAccessToken::GetThreadToken](#getthreadtoken), sino que establece el nivel de suplantación antes de inicializar el `CAccessToken` del token de acceso del subproceso.  
  
 El [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md) puede utilizarse para invertir automáticamente los tokens de acceso suplantado creados estableciendo la `bImpersonate` indicador en *true*.  
  
##  <a name="privilegecheck"></a>CAccessToken::PrivilegeCheck  
 Llamar a este método para determinar si se habilita un conjunto especificado de privilegios en el **CAccessToken** objeto.  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *RequiredPrivileges*  
 Puntero a un [PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307) estructura.  
  
 *pbResult*  
 Puntero a un valor que el método establece para indicar si alguno o todos los privilegios especificados están habilitadas en el `CAccessToken` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `PrivilegeCheck` devuelve, la **atributos** miembro de cada [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263) estructura se establece en SE_PRIVILEGE_USED_FOR_ACCESS si está habilitado el privilegio correspondiente. Este método llama a la [PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) función de Win32.  
  
##  <a name="revert"></a>CAccessToken::Revert  
 Llamar a este método para detener un subproceso del uso de un token de suplantación.  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hThread`  
 Identificador para el subproceso para revertir de suplantación. Si *hThread* es NULL, se supone que el subproceso actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 La reversión de tokens de suplantación se puede realizar automáticamente con el [CAutoRevertImpersonation clase](../../atl/reference/cautorevertimpersonation-class.md).  
  
##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl  
 Llamar a este método para establecer el valor predeterminado DACL de la `CAccessToken` objeto.  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rDacl`  
 El nuevo valor predeterminado [CDacl clase](../../atl/reference/cdacl-class.md) información.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 La DACL predeterminada es la DACL que se utiliza de forma predeterminada cuando se creen nuevos objetos con este token de acceso en vigor.  
  
##  <a name="setowner"></a>CAccessToken::SetOwner  
 Llamar a este método para establecer el propietario de la `CAccessToken` objeto.  
  
```
bool SetOwner(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 El [CSid clase](../../atl/reference/csid-class.md) que contiene la información del propietario del objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El propietario es el propietario predeterminado que se usa para los nuevos objetos creados mientras este token de acceso está en vigor.  
  
##  <a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup  
 Llamar a este método para establecer el grupo primario de la `CAccessToken` objeto.  
  
```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parámetros  
 `rSid`  
 El [CSid clase](../../atl/reference/csid-class.md) objeto que contiene la información de grupo principal.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la operación se realiza correctamente; de lo contrario, devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 El grupo principal es el grupo predeterminado para nuevos objetos creados mientras este token de acceso está en vigor.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo ATLSecurity](../../visual-cpp-samples.md)   
 [Tokens de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Información general de clases](../../atl/atl-class-overview.md)
