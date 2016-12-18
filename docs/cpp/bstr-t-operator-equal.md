---
title: "_bstr_t::operator = | Microsoft Docs"
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
  - "_bstr_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= (operador), con objetos específicos de Visual C++"
  - "operador =, bstr"
  - "operator=, bstr"
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Asigna un nuevo valor a un objeto `_bstr_t` existente.  
  
## Sintaxis  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### Parámetros  
 *s1*  
 Un objeto `_bstr_t` que se va a asignar a un objeto `_bstr_t` existente.  
  
 *s2*  
 Una cadena multibyte que se va a asignar a un objeto `_bstr_t` existente.  
  
 `s3`  
 Una cadena Unicode que se va a asignar a un objeto `_bstr_t` existente.  
  
 `var`  
 Un objeto `_variant_t` que se va a asignar a un objeto `_bstr_t` existente.  
  
 **FIN de Específicos de Microsoft**  
  
## Ejemplo  
 Vea [\_bstr\_t::Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de `operator=`.  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)