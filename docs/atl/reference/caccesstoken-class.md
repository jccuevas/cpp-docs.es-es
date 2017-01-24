---
title: "CAccessToken Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATLSECURITY/CAccessToken"
  - "ATL.CAccessToken"
  - "CAccessToken"
  - "ATL::CAccessToken"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessToken class"
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessToken Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor para un token de acceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAccessToken  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccessToken::~CAccessToken](../Topic/CAccessToken::~CAccessToken.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccessToken::Attach](../Topic/CAccessToken::Attach.md)|Llame a este método para realizar la propiedad ID especificado del token de acceso.|  
|[CAccessToken::CheckTokenMembership](../Topic/CAccessToken::CheckTokenMembership.md)|Llame a este método para determinar si un SID especificado está habilitada en el objeto de `CAccessToken` .|  
|[CAccessToken::CreateImpersonationToken](../Topic/CAccessToken::CreateImpersonationToken.md)|Llame a este método para crear un nuevo token de acceso de la suplantación.|  
|[CAccessToken::CreatePrimaryToken](../Topic/CAccessToken::CreatePrimaryToken.md)|Llame a este método para crear un nuevo token primario.|  
|[CAccessToken::CreateProcessAsUser](../Topic/CAccessToken::CreateProcessAsUser.md)|Llame a este método para crear un nuevo proceso que se ejecuta en el contexto de seguridad del usuario representado por el objeto de `CAccessToken` .|  
|[CAccessToken::CreateRestrictedToken](../Topic/CAccessToken::CreateRestrictedToken.md)|Llame a este método para crear un nuevo, restringido objeto de `CAccessToken` .|  
|[CAccessToken::Detach](../Topic/CAccessToken::Detach.md)|Llame a este método para revocar la propiedad del token de acceso.|  
|[CAccessToken::DisablePrivilege](../Topic/CAccessToken::DisablePrivilege.md)|Llame a este método para deshabilitar un privilegio en el objeto de `CAccessToken` .|  
|[CAccessToken::DisablePrivileges](../Topic/CAccessToken::DisablePrivileges.md)|Llame a este método para deshabilitar uno o más privilegios en el objeto de `CAccessToken` .|  
|[CAccessToken::EnablePrivilege](../Topic/CAccessToken::EnablePrivilege.md)|Llame a este método para habilitar un privilegio en el objeto de `CAccessToken` .|  
|[CAccessToken::EnablePrivileges](../Topic/CAccessToken::EnablePrivileges.md)|Llame a este método para habilitar uno o más privilegios en el objeto de `CAccessToken` .|  
|[CAccessToken::GetDefaultDacl](../Topic/CAccessToken::GetDefaultDacl.md)|Llame a este método para devolver una DACL de objeto predeterminado de `CAccessToken` .|  
|[CAccessToken::GetEffectiveToken](../Topic/CAccessToken::GetEffectiveToken.md)|Llame a este método para obtener el objeto de `CAccessToken` igual al token de acceso en vigor para el subproceso actual.|  
|[CAccessToken::GetGroups](../Topic/CAccessToken::GetGroups.md)|Llame a este método para devolver grupos token de objeto de `CAccessToken` .|  
|[CAccessToken::GetHandle](../Topic/CAccessToken::GetHandle.md)|Llame a este método para recuperar un identificador al token de acceso.|  
|[CAccessToken::GetImpersonationLevel](../Topic/CAccessToken::GetImpersonationLevel.md)|Llame a este método para obtener el nivel de suplantación del token de acceso.|  
|[CAccessToken::GetLogonSessionId](../Topic/CAccessToken::GetLogonSessionId.md)|Llame a este método para obtener el Id. de sesión de inicio de sesión asociado al objeto de `CAccessToken` .|  
|[CAccessToken::GetLogonSid](../Topic/CAccessToken::GetLogonSid.md)|Llame a este método para obtener el inicio de sesión SID asociado al objeto de `CAccessToken` .|  
|[CAccessToken::GetOwner](../Topic/CAccessToken::GetOwner.md)|Llame a este método para obtener el propietario asociado al objeto de `CAccessToken` .|  
|[CAccessToken::GetPrimaryGroup](../Topic/CAccessToken::GetPrimaryGroup.md)|Llame a este método para obtener el grupo primario asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::GetPrivileges](../Topic/CAccessToken::GetPrivileges.md)|Llame a este método para obtener los privilegios asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::GetProcessToken](../Topic/CAccessToken::GetProcessToken.md)|Llame a este método para inicializar `CAccessToken` con el token de acceso del proceso especificado.|  
|[CAccessToken::GetProfile](../Topic/CAccessToken::GetProfile.md)|Llame a este método para obtener el identificador del perfil de usuario asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::GetSource](../Topic/CAccessToken::GetSource.md)|Llame a este método para obtener el origen de objetos de `CAccessToken` .|  
|[CAccessToken::GetStatistics](../Topic/CAccessToken::GetStatistics.md)|Llame a este método para obtener la información asociada con el objeto de `CAccessToken` .|  
|[CAccessToken::GetTerminalServicesSessionId](../Topic/CAccessToken::GetTerminalServicesSessionId.md)|Llame a este método para obtener el identificador de sesión de Terminal services asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::GetThreadToken](../Topic/CAccessToken::GetThreadToken.md)|Llame a este método para inicializar `CAccessToken` con el símbolo del subproceso especificado.|  
|[CAccessToken::GetTokenId](../Topic/CAccessToken::GetTokenId.md)|Llame a este método para obtener el identificador del token asociado al objeto de `CAccessToken` .|  
|[CAccessToken::GetType](../Topic/CAccessToken::GetType.md)|Llame a este método para obtener el tipo de token del objeto de `CAccessToken` .|  
|[CAccessToken::GetUser](../Topic/CAccessToken::GetUser.md)|Llame a este método para identificar al usuario asociado al objeto de `CAccessToken` .|  
|[CAccessToken::HKeyCurrentUser](../Topic/CAccessToken::HKeyCurrentUser.md)|Llame a este método para obtener el identificador del perfil de usuario asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::Impersonate](../Topic/CAccessToken::Impersonate.md)|Llame a este método para asignar una suplantación `CAccessToken` a un subproceso.|  
|[CAccessToken::ImpersonateLoggedOnUser](../Topic/CAccessToken::ImpersonateLoggedOnUser.md)|Llame a este método para permitir que el subproceso de llamada suplantar el contexto de seguridad de un usuario registrado.|  
|[CAccessToken::IsTokenRestricted](../Topic/CAccessToken::IsTokenRestricted.md)|Llame a este método para comprobar si el objeto de `CAccessToken` contiene una lista de SID restringidos.|  
|[CAccessToken::LoadUserProfile](../Topic/CAccessToken::LoadUserProfile.md)|Llame a este método para cargar el perfil de usuario asociado con el objeto de `CAccessToken` .|  
|[CAccessToken::LogonUser](../Topic/CAccessToken::LogonUser.md)|Llame a este método para crear una sesión de inicio de sesión del usuario asociado con las credenciales especificadas.|  
|[CAccessToken::OpenCOMClientToken](../Topic/CAccessToken::OpenCOMClientToken.md)|Llame a este método en un servidor COM que administra una llamada de un cliente para inicializar `CAccessToken` con el token de acceso de cliente COM.|  
|[CAccessToken::OpenNamedPipeClientToken](../Topic/CAccessToken::OpenNamedPipeClientToken.md)|Llame a este método en un servidor que toma las solicitudes sobre una canalización con nombre para inicializar `CAccessToken` con el token de acceso de cliente.|  
|[CAccessToken::OpenRPCClientToken](../Topic/CAccessToken::OpenRPCClientToken.md)|Llame a este método en un servidor que administra una llamada de un cliente RPC para inicializar `CAccessToken` con el token de acceso de cliente.|  
|[CAccessToken::OpenThreadToken](../Topic/CAccessToken::OpenThreadToken.md)|Llame a este método para establecer el nivel de suplantación y después para inicializar `CAccessToken` con el símbolo del subproceso especificado.|  
|[CAccessToken::PrivilegeCheck](../Topic/CAccessToken::PrivilegeCheck.md)|Llame a este método para determinar si habilitan un conjunto especificado de privilegios en el objeto de **CAccessToken** .|  
|[CAccessToken::Revert](../Topic/CAccessToken::Revert.md)|Llame a este método para detener un subproceso que está utilizando un token de representación.|  
|[CAccessToken::SetDefaultDacl](../Topic/CAccessToken::SetDefaultDacl.md)|Llame a este método para establecer una DACL de objeto predeterminado de `CAccessToken` .|  
|[CAccessToken::SetOwner](../Topic/CAccessToken::SetOwner.md)|Llame a este método para establecer el propietario del objeto de `CAccessToken` .|  
|[CAccessToken::SetPrimaryGroup](../Topic/CAccessToken::SetPrimaryGroup.md)|Llame a este método para establecer el grupo primario del objeto de `CAccessToken` .|  
  
## Comentarios  
 [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o de un subproceso y se asigna a cada usuario registrado en un sistema de Windows NT o Windows 2000.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo ATLSecurity](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)