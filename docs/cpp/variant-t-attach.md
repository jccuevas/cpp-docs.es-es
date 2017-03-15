---
title: "_variant_t::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::Attach"
  - "_variant_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach (método)"
  - "VARIANT (objeto)"
  - "VARIANT (objeto), asociar"
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Adjunta un objeto **VARIANT** al objeto `_variant_t`.  
  
## Sintaxis  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### Parámetros  
 *varSrc*  
 Objeto **VARIANT** que se adjuntará a este objeto `_variant_t`.  
  
## Comentarios  
 Toma la propiedad de **VARIANT** encapsulándolo.  Esta función miembro libera cualquier **VARIANT** encapsulado existente, copia el **VARIANT** proporcionado y establece su **VARTYPE** en `VT_EMPTY` para garantizar que solo el destructor `_variant_t` puede liberar sus recursos.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)