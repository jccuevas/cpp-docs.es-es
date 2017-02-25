---
title: "_com_ptr_t::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::Detach"
  - "_com_ptr_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach (método)"
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_ptr_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Extrae y devuelve el puntero de interfaz encapsulado.  
  
## Sintaxis  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## Comentarios  
 Extrae y devuelve el puntero de interfaz encapsulado y, a continuación, borra el almacenamiento del puntero encapsulado como **NULL**.  Esto quita el puntero de interfaz de la encapsulación.  Decida si desea o no llamar a **Release** en el puntero de interfaz devuelto.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)