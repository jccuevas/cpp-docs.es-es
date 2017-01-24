---
title: "RaiseException (Funci&#243;n) | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::RaiseException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RaiseException (función)"
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RaiseException (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
inline void __declspec(noreturn)  
   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### Parámetros  
 `hr`  
 El código de excepción de la excepción que se desencadena; es decir, el valor HRESULT de una operación con errores.  
  
 `dwExceptionFlags`  
 Una marca que indica una excepción continuado \(el valor del marcador es cero\), o excepción noncontinuable \(el valor del marcador es distinto de cero\).  De forma predeterminada, la excepción se noncontinuable.  
  
## Comentarios  
 Produce una excepción en el subproceso de llamada.  
  
 Para obtener más información, vea la función de Windows **RaiseException** .  
  
## Requisitos  
 **Encabezado:** internal.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)