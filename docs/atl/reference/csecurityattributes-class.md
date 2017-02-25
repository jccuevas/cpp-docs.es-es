---
title: "CSecurityAttributes Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSecurityAttributes"
  - "ATL::CSecurityAttributes"
  - "CSecurityAttributes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSecurityAttributes class"
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CSecurityAttributes Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor fino para la estructura de los atributos de seguridad.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CSecurityAttributes : public SECURITY_ATTRIBUTES  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](../Topic/CSecurityAttributes::CSecurityAttributes.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSecurityAttributes::Set](../Topic/CSecurityAttributes::Set.md)|Llame a este método para establecer los atributos del objeto de `CSecurityAttributes` .|  
  
## Comentarios  
 La estructura de **SECURITY\_ATTRIBUTES** contiene [descriptor de seguridad](http://msdn.microsoft.com/library/windows/desktop/aa379561) utilizado para la creación de un objeto y especifica si el identificador recuperado especificando esta estructura se puede heredar.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo de seguridad](../../top/visual-cpp-samples.md)   
 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [security descriptor](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Security Global Functions](../../atl/reference/security-global-functions.md)