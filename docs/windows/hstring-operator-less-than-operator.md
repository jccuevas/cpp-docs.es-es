---
title: "HString::Operator&lt; (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::operator<"
dev_langs: 
  - "C++"
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Operator&lt; (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si el primer parámetro es menor que el segundo parámetro.  
  
## Sintaxis  
  
```cpp  
  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### Parámetros  
 `lhs`  
 El primer parámetro a comparar.  `lhs` puede ser una referencia a un HString.  
  
 `rhs`  
 El segundo parámetro a comparar.  `rhs` puede ser una referencia a un HString.  
  
## Valor devuelto  
 `true` si el parámetro de `lhs` es menor que el parámetro de `rhs` ; si no, `false`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HString \(Clase\)](../windows/hstring-class.md)