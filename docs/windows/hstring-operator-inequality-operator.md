---
title: "HString::Operator!= (Operador) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::operator!="
dev_langs: 
  - "C++"
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Operator!= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si los dos parámetros no son iguales.  
  
## Sintaxis  
  
```cpp  
  
   inline bool operator!=(  
                  const HString& lhs,   
                  const HString& rhs) throw()  
  
inline bool operator!=(  
                  const HStringReference& lhs,   
                  const HString& rhs) throw()  
  
inline bool operator!=(  
                  const HString& lhs,   
                  const HStringReference& rhs) throw()  
  
inline bool operator!=(  
                  const HSTRING& lhs,   
                  const HString& rhs) throw()  
  
inline bool operator!=(  
                  const HString& lhs,   
                  const HSTRING& rhs) throw()  
  
```  
  
#### Parámetros  
 `lhs`  
 El primer parámetro a comparar.  `lhs` puede ser un objeto de HString o de HStringReference, o un identificador de HSTRING.  
  
 `rhs`  
 El segundo parámetro a comparar.`rhs` puede ser un objeto de HString o de HStringReference, o un identificador de HSTRING.  
  
## Valor devuelto  
 Es `true` si los parámetros `lhs` y `rhs` no son iguales; en caso contrario, es `false`.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HString \(Clase\)](../windows/hstring-class.md)