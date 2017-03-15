---
title: "AsyncResultType (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncResultType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncResultType (enumeración)"
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncResultType (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el tipo de resultado devuelto por el método de GetResults\(\) .  
  
## Sintaxis  
  
```  
enum AsyncResultType;  
```  
  
## Miembros  
  
### Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`MultipleResults`|Un conjunto de resultados múltiples, que se muestran progresivamente entre el estado inicial y antes de llamar a Close\(\) .|  
|`SingleResult`|Un solo resultado, que se muestra después de que el evento completed aparece.|  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)