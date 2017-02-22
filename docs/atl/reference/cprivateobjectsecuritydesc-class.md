---
title: "CPrivateObjectSecurityDesc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPrivateObjectSecurityDesc"
  - "ATL::CPrivateObjectSecurityDesc"
  - "CPrivateObjectSecurityDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrivateObjectSecurityDesc class"
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CPrivateObjectSecurityDesc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase representa un objeto de descriptor de seguridad privado del objeto.  
  
## Sintaxis  
  
```  
  
class CPrivateObjectSecurityDesc : public CSecurityDesc  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc.md)|el constructor.|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](../Topic/CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](../Topic/CPrivateObjectSecurityDesc::ConvertToAutoInherit.md)|Llame a este método para convertir un descriptor de seguridad y las listas \(ACLs\) de control de acceso a un formato que admita la propagación de entradas de control de acceso heredable \(ACEs\).|  
|[CPrivateObjectSecurityDesc::Create](../Topic/CPrivateObjectSecurityDesc::Create.md)|Llame a este método para asignar y para inicializar un descriptor de seguridad uno mismo\- relativo para el objeto privado creado por el administrador de recursos de la llamada.|  
|[CPrivateObjectSecurityDesc::Get](../Topic/CPrivateObjectSecurityDesc::Get.md)|Llame a este método para recuperar información del descriptor de seguridad de un objeto privado.|  
|[CPrivateObjectSecurityDesc::Set](../Topic/CPrivateObjectSecurityDesc::Set.md)|Llame a este método para modificar el descriptor de seguridad de un objeto privado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/CPrivateObjectSecurityDesc::operator%20=.md)|Operador de asignación.|  
  
## Comentarios  
 Esta clase, derivada de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), proporciona métodos para crear y administrar el descriptor de seguridad de un objeto privado.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [SECURITY\_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)   
 [CSecurityDesc Class](../../atl/reference/csecuritydesc-class.md)