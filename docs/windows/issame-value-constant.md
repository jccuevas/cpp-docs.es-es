---
title: "IsSame::value (Constante) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::IsSame::value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value (constante)"
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsSame::value (Constante)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <typename T1, typename T2>  
    struct IsSame  
    {  
        static const bool value = false;  
    };  
  
    template <typename T1>  
    struct IsSame<T1, T1>  
    {  
        static const bool value = true;  
    };  
  
```  
  
## Comentarios  
 Indica si un tipo es igual que otro.  
  
 `value` es **true** si los parámetros de plantilla son iguales, y **false** si los parámetros de plantilla son diferentes.  
  
## Requisitos  
 **Encabezado:** internal.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [IsSame \(Estructura\)](../windows/issame-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)