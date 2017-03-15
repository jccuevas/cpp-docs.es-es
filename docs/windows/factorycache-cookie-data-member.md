---
title: "FactoryCache::cookie (Miembro de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::FactoryCache::cookie"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cookie (miembro de datos)"
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# FactoryCache::cookie (Miembro de datos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es compatible con la infraestructura de [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] y no está diseñado para que se utilice directamente desde el código.  
  
## Sintaxis  
  
```  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## Comentarios  
 Contiene un valor que identifica [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] o un objeto registrado de la clase COM, y se utiliza después para anular el registro del objeto.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [FactoryCache \(Estructura\)](../Topic/FactoryCache%20Structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)