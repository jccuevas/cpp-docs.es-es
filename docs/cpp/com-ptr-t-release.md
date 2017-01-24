---
title: "_com_ptr_t::Release | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t.Release"
  - "_com_ptr_t::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release (método)"
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función miembro **Release** de **IUnknown** en el puntero de interfaz encapsulado.  
  
## Sintaxis  
  
```  
  
void Release( );  
  
```  
  
## Comentarios  
 Llama a `IUnknown::Release` en el puntero encapsulado de interfaz y genera un error `E_POINTER` si este puntero de interfaz es **NULL**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)