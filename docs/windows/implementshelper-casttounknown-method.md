---
title: "ImplementsHelper::CastToUnknown (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown (método)"
ms.assetid: 5bcfcbaf-c75f-4d43-87b3-0d6838c838d9
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ImplementsHelper::CastToUnknown (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
IUnknown* CastToUnknown();  
```  
  
## Valor devuelto  
 Puntero a la interfaz subyacente de IUnknown.  
  
## Comentarios  
 Obtiene un puntero al IUnknown subyacente que la interfaz del actual implementa la estructura.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ImplementsHelper \(Estructura\)](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)