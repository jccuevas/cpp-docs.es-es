---
title: "_com_ptr_t::Attach | Microsoft Docs"
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
  - "_com_ptr_t::Attach"
  - "_com_ptr_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach (método)"
  - "interfaces COM, asociar puntero"
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.  
  
## Sintaxis  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### Parámetros  
 `pInterface`  
 Puntero a interfaz sin formato.  
  
 `fAddRef`  
 Si es **true**, se llama a `AddRef`.  Si es **false**, el objeto `_com_ptr_t` toma propiedad del puntero de interfaz sin formato sin llamar a `AddRef`.  
  
## Comentarios  
  
-   **Attach\(**  `pInterface`  **\)** No se llama a `AddRef`.  La propiedad de la interfaz se pasa a este objeto `_com_ptr_t`.  Se llama a **release** para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
-   **Attach\(**  `pInterface` **,**  `fAddRef`  **\)** Si `fAddRef` es **true**, se llama a `AddRef` para incrementar el recuento de referencias del puntero de interfaz encapsulado.  Si `fAddRef` es **false**, este objeto `_com_ptr_t` toma propiedad del puntero de interfaz sin formato sin llamar a `AddRef`.  Se llama a **release** para disminuir el recuento de referencias para el puntero previamente encapsulado.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)