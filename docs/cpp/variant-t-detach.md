---
title: "_variant_t::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::Detach"
  - "_variant_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach (método)"
  - "VARIANT (objeto)"
  - "VARIANT (objeto), desasociar"
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# _variant_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Desasocia el objeto **VARIANT** encapsulado de este objeto `_variant_t`.  
  
## Sintaxis  
  
```  
  
VARIANT Detach( );  
  
```  
  
## Valor devuelto  
 El objeto **VARIANT** encapsulado.  
  
## Comentarios  
 Extrae y devuelve el objeto **VARIANT** encapsulado y, a continuación, borra este objeto `_variant_t` sin destruirlo.  Esta función miembro quita el objeto **VARIANT** de la encapsulación y establece el **VARTYPE** de este objeto `_variant_t` en `VT_EMPTY`.  Decida si va a liberar el objeto **VARIANT** devuelto llamando a la función [VariantClear](http://msdn.microsoft.com/es-es/28741d81-8404-4f85-95d3-5c209ec13835).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)