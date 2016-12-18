---
title: "HStringReference::Operator= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mueve el valor de otro objeto HStringReference al objeto HStringReference actual.  
  
## Sintaxis  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### Parámetros  
 `other`  
 Un objeto existente de HStringReference.  
  
## Comentarios  
 El valor del objeto existente de `other` se copia en el objeto actual de HStringReference, y el objeto de `other` se destruye.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HStringReference \(Clase\)](../windows/hstringreference-class.md)