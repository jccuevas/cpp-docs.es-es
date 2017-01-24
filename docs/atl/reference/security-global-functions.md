---
title: "Security Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ACL object global functions"
  - "security IDs [C++]"
  - "SIDs [C++], modifying SID objects"
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Security Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan compatibilidad para modificar objetos de SID y ACL.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlGetDacl](../Topic/AtlGetDacl.md)|Llame a esta función para recuperar la información \(DACL\) de la lista de control de acceso discrecional \(DACL\) de un objeto especificado.|  
|[AtlSetDacl](../Topic/AtlSetDacl.md)|Llame a esta función para establecer la información \(DACL\) de la lista de control de acceso discrecional \(DACL\) de un objeto especificado.|  
|[AtlGetGroupSid](../Topic/AtlGetGroupSid.md)|Llame a esta función para recuperar el identificador de seguridad del \(SID\) grupo de un objeto.|  
|[AtlSetGroupSid](../Topic/AtlSetGroupSid.md)|Llame a esta función para establecer el identificador de seguridad del \(SID\) grupo de un objeto.|  
|[AtlGetOwnerSid](../Topic/AtlGetOwnerSid.md)|Llame a esta función para recuperar el identificador de seguridad del propietario \(SID\) de un objeto.|  
|[AtlSetOwnerSid](../Topic/AtlSetOwnerSid.md)|Llame a esta función para establecer el identificador de seguridad del propietario \(SID\) de un objeto.|  
|[AtlGetSacl](../Topic/AtlGetSacl.md)|Llame a esta función para recuperar la información \(SACL\) de la lista de control de acceso del sistema de un objeto especificado.|  
|[AtlSetSacl](../Topic/AtlSetSacl.md)|Llame a esta función para establecer la información \(SACL\) de la lista de control de acceso del sistema de un objeto especificado.|  
|[AtlGetSecurityDescriptor](../Topic/AtlGetSecurityDescriptor.md)|Llame a esta función para recuperar el descriptor de seguridad de un objeto determinado.|  
  
## Vea también  
 [Funciones](../../atl/reference/atl-functions.md)