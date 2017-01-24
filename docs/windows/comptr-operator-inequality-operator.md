---
title: "ComPtr::operator!= (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator!="
dev_langs: 
  - "C++"
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator!= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si dos objetos de ComPtr no son iguales.  
  
## Sintaxis  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### Parámetros  
 `a`  
 Una referencia a un objeto de ComPtr.  
  
 `b`  
 Una referencia a otro objeto de ComPtr.  
  
## Valor devuelto  
 El primer operador produce `true` si el objeto `a` no es igual al objeto `b`; si no, `false`.  
  
 El segundo y tercer operadores producen `true` si el objeto `a` no es igual a `nullptr`; si no, `false`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)   
 [ComPtr \(Clase\)](../windows/comptr-class.md)