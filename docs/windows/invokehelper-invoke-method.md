---
title: "InvokeHelper::Invoke (M&#233;todo) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::InvokeHelper::Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Invoke (método)"
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InvokeHelper::Invoke (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
#### Parámetros  
 `arg1`  
 Argumento 1.  
  
 `arg2`  
 Argumento 2.  
  
 `arg3`  
 Argumento 3.  
  
 `arg4`  
 Argumento 4.  
  
 `arg5`  
 Argumento 5.  
  
 `arg6`  
 Argumento 6.  
  
 `arg7`  
 Argumento 7.  
  
 `arg8`  
 Argumento 8.  
  
 `arg9`  
 Argumento 9.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  
  
## Comentarios  
 Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [InvokeHelper \(Estructura\)](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)