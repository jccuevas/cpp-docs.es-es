---
title: "_variant_t::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::ChangeType"
  - "_variant_t.ChangeType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChangeType (método)"
  - "VARIANT (objeto)"
  - "VARIANT (objeto), ChangeType"
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t::ChangeType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Cambia el tipo del objeto `_variant_t` al **VARTYPE** indicado.  
  
## Sintaxis  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### Parámetros  
 `vartype`  
 El **VARTYPE** para este `_variant_t` objeto.  
  
 `pSrc`  
 Un puntero al objeto `_variant_t` que se va a convertir.  Si este valor es **NULL**, la conversión se realiza en contexto.  
  
## Comentarios  
 Esta función miembro convierte un objeto `_variant_t` en el **VARTYPE**indicado.  Si `pSrc` es **NULL**, la conversión se realiza en contexto; de lo contrario, este objeto `_variant_t` se copia de `pSrc` y después se convierte.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)