---
title: "ComPtrRef::operator== (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator=="
dev_langs: 
  - "C++"
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator== (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```cpp  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### Parámetros  
 `a`  
 Una referencia a un objeto de ComPtrRef.  
  
 `b`  
 Una referencia a otro objeto de ComPtrRef, o un puntero a un tipo anónimo \(`void*`\).  
  
## Valor devuelto  
 El primer operador produce `true` si el objeto `a` es igual al objeto `b`; si no, `false`.  
  
 El segundo y tercer operadores producen `true` si el objeto `a` es igual a `nullptr`; si no, `false`.  
  
 Los cuartos y quintos operadores producen `true` si el objeto `a` es igual al objeto `b`; si no, `false`.  
  
## Comentarios  
 Indica si dos objetos de ComPtrRef son iguales.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef \(Clase\)](../Topic/ComPtrRef%20Class.md)