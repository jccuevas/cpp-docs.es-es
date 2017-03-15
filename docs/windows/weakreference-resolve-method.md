---
title: "WeakReference::Resolve (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::Resolve"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Resolve (método)"
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakReference::Resolve (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### Parámetros  
 `riid`  
 Un identificador de interfaz  
  
 `ppvObject`  
 Cuando esta operación completa, una copia de la referencia segura actual si el recuento de referencia es distinto de cero.  
  
## Valor devuelto  
  
-   S\_OK si esta operación es correcta y el recuento seguros de referencia es cero.  El valor del parámetro `ppvObject` se establece en `nullptr`.  
  
-   S\_OK si esta operación es correcta y el recuento seguros de referencia es distinto de cero.  El parámetro de `ppvObject` se establece en la referencia segura.  
  
-   Si no, un HRESULT que indica la razón esta operación no.  
  
## Comentarios  
 Establece el puntero especificado en el valor de referencia segura actual si el recuento de referencia es distinto de cero.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [WeakReference \(Clase\)](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)