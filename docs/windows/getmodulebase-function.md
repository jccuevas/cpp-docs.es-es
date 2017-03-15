---
title: "GetModuleBase (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::GetModuleBase"
dev_langs: 
  - "C++"
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# GetModuleBase (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera un puntero de [ModuleBase](../windows/modulebase-class.md) que permite aumentar y disminuir el recuento de referencias de un objeto de [RuntimeClass](../windows/runtimeclass-class.md) .  
  
## Sintaxis  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## Valor devuelto  
 Un puntero a un objeto de `ModuleBase` .  
  
## Comentarios  
 Esta función se utiliza internamente para incrementar y para reducir los recuentos de referencia de objeto.  
  
 Puede utilizar esta función para controlar los recuentos de referencias llamando a [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) y [ModuleBase::DecrementObjectCount](../Topic/ModuleBase::DecrementObjectCount%20Method.md).  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)