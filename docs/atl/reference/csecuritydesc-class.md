---
title: "CSecurityDesc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSecurityDesc"
  - "ATL.CSecurityDesc"
  - "CSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSecurityDesc class"
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase es un contenedor para la estructura de **SECURITY\_DESCRIPTOR** .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CSecurityDesc  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::CSecurityDesc](../Topic/CSecurityDesc::CSecurityDesc.md)|el constructor.|  
|[CSecurityDesc::~CSecurityDesc](../Topic/CSecurityDesc::~CSecurityDesc.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::FromString](../Topic/CSecurityDesc::FromString.md)|Convierte un descriptor de seguridad de cadena\- formato en un descriptor de seguridad válido, funcional.|  
|[CSecurityDesc::GetControl](../Topic/CSecurityDesc::GetControl.md)|Recupera información de control del descriptor de seguridad.|  
|[CSecurityDesc::GetDacl](../Topic/CSecurityDesc::GetDacl.md)|Recupera la información \(DACL\) de la lista de control de acceso discrecional \(DACL\) del descriptor de seguridad.|  
|[CSecurityDesc::GetGroup](../Topic/CSecurityDesc::GetGroup.md)|Recupera información del grupo primario de descriptor de seguridad.|  
|[CSecurityDesc::GetOwner](../Topic/CSecurityDesc::GetOwner.md)|Recupera el informaton propietario del descriptor de seguridad.|  
|[CSecurityDesc::GetPSECURITY\_DESCRIPTOR](../Topic/CSecurityDesc::GetPSECURITY_DESCRIPTOR.md)|devuelve un puntero a la estructura de **SECURITY\_DESCRIPTOR** .|  
|[CSecurityDesc::GetSacl](../Topic/CSecurityDesc::GetSacl.md)|Recupera información de \(SACL\) de la lista de control de acceso del sistema del descriptor de seguridad.|  
|[CSecurityDesc::IsDaclAutoInherited](../Topic/CSecurityDesc::IsDaclAutoInherited.md)|Determina si una DACL se configura para admitir la propagación.|  
|[CSecurityDesc::IsDaclDefaulted](../Topic/CSecurityDesc::IsDaclDefaulted.md)|Determina si el descriptor de seguridad con una DACL predeterminado.|  
|[CSecurityDesc::IsDaclPresent](../Topic/CSecurityDesc::IsDaclPresent.md)|Determina si el descriptor de seguridad contiene una DACL.|  
|[CSecurityDesc::IsDaclProtected](../Topic/CSecurityDesc::IsDaclProtected.md)|Determina si una DACL se configura para evitar modificaciones.|  
|[CSecurityDesc::IsGroupDefaulted](../Topic/CSecurityDesc::IsGroupDefaulted.md)|Determina si el identificador de seguridad del grupo del descriptor de seguridad \(SID\) se establece de forma predeterminada.|  
|[CSecurityDesc::IsOwnerDefaulted](../Topic/CSecurityDesc::IsOwnerDefaulted.md)|Determina si establecieron el propietario SID de descriptor de seguridad de forma predeterminada.|  
|[CSecurityDesc::IsSaclAutoInherited](../Topic/CSecurityDesc::IsSaclAutoInherited.md)|Determina si SACL se configura para admitir la propagación.|  
|[CSecurityDesc::IsSaclDefaulted](../Topic/CSecurityDesc::IsSaclDefaulted.md)|Determina si el descriptor de seguridad con SACL predeterminado.|  
|[CSecurityDesc::IsSaclPresent](../Topic/CSecurityDesc::IsSaclPresent.md)|Determina si el descriptor de seguridad contiene SACL.|  
|[CSecurityDesc::IsSaclProtected](../Topic/CSecurityDesc::IsSaclProtected.md)|Determina si SACL se configura para evitar modificaciones.|  
|[CSecurityDesc::IsSelfRelative](../Topic/CSecurityDesc::IsSelfRelative.md)|Determina si el descriptor de seguridad está en formato uno mismo\-relativo.|  
|[CSecurityDesc::MakeAbsolute](../Topic/CSecurityDesc::MakeAbsolute.md)|Llame a este método para convertir un descriptor de seguridad al formato absoluto.|  
|[CSecurityDesc::MakeSelfRelative](../Topic/CSecurityDesc::MakeSelfRelative.md)|Llame a este método para convertir un descriptor de seguridad al formato uno mismo\- relativo.|  
|[CSecurityDesc::SetControl](../Topic/CSecurityDesc::SetControl.md)|Establece los bits del control de un descriptor de seguridad.|  
|[CSecurityDesc::SetDacl](../Topic/CSecurityDesc::SetDacl.md)|Establece la información en una DACL.  Si una DACL ya está presente en el descriptor de seguridad, se reemplaza.|  
|[CSecurityDesc::SetGroup](../Topic/CSecurityDesc::SetGroup.md)|Establece la información del grupo primario de un descriptor de seguridad absoluto de formato, reemplazando cualquier presente de información de grupo primario ya.|  
|[CSecurityDesc::SetOwner](../Topic/CSecurityDesc::SetOwner.md)|Establece la información de propietario de un descriptor de seguridad absoluto de formato, reemplazando cualquier presente de información de propietario ya.|  
|[CSecurityDesc::SetSacl](../Topic/CSecurityDesc::SetSacl.md)|Establece la información en SACL.  Si una SACL ya está presente en el descriptor de seguridad, se reemplaza.|  
|[CSecurityDesc::ToString](../Topic/CSecurityDesc::ToString.md)|Convierte un descriptor de seguridad a un formato de cadena.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY\_DESCRIPTOR \*](../Topic/CSecurityDesc::operator%20const%20SECURITY_DESCRIPTOR%20*.md)|devuelve un puntero a la estructura de **SECURITY\_DESCRIPTOR** .|  
|[CSecurityDesc::operator \=](../Topic/CSecurityDesc::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 La estructura de **SECURITY\_DESCRIPTOR** contiene información de seguridad asociado a un objeto.  Las aplicaciones utilizan esta estructura para establecer y ver el estado de seguridad de un objeto.  Vea también [AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md).  
  
 Las aplicaciones no deben modificar la estructura de **SECURITY\_DESCRIPTOR** directamente y, en su lugar deben utilizar los métodos de clase proporcionados.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)