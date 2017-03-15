---
title: "RuntimeClass::GetIids (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetIids"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetIids (método)"
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetIids (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una matriz que contenga los id. de la interfaz implementados por el objeto actual de RuntimeClass.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### Parámetros  
 `iidCount`  
 Cuando esta operación finaliza, el número total de elementos de la matriz `iids`.  
  
 `iids`  
 Cuando esta operación finaliza, un puntero a una matriz de id. de la interfaz.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_OUTOFMEMORY.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [RuntimeClass \(Clase\)](../windows/runtimeclass-class.md)