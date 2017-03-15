---
title: "ModuleBase::IncrementObjectCount (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncrementObjectCount (método)"
ms.assetid: 2d70b472-684c-4bb7-8bab-09505cfcaf28
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ModuleBase::IncrementObjectCount (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
virtual long IncrementObjectCount() = 0;  
```  
  
## Valor devuelto  
 El recuento antes de la operación de incremento.  
  
## Comentarios  
 Cuando se implementa, se incrementa el número de objetos seguidos del módulo.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ModuleBase \(Clase\)](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)