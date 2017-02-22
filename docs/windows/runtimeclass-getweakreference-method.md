---
title: "RuntimeClass::GetWeakReference (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetWeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetWeakReference (método)"
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetWeakReference (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene un puntero al objeto débil de referencia para el objeto actual de RuntimeClass.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetWeakReference  
)(_Deref_out_ IWeakReference **weakReference);  
```  
  
#### Parámetros  
 `weakReference`  
 Cuando esta operación finaliza, un puntero a un objeto débil de referencia.  
  
## Valor devuelto  
 Siempre S\_OK.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [RuntimeClass \(Clase\)](../windows/runtimeclass-class.md)