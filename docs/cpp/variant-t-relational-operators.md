---
title: "_variant_t (Operadores relacionales) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::operator=="
  - "_variant_t.operator!="
  - "_variant_t::operator!="
  - "_variant_t.operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= (operador)"
  - "== (operador), con objetos específicos de Visual C++"
  - "operador !=, operadores relacionales"
  - "operador !=, variante"
  - "operador ==, variante"
  - "operator!=, operadores relacionales"
  - "operator!=, variante"
  - "operator==, variante"
  - "operadores relacionales, _variant_t (clase)"
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t (Operadores relacionales)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Compara dos objetos `_variant_t` para ver si son iguales o no.  
  
## Sintaxis  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### Parámetros  
 *varSrc*  
 **VARIANT** que se va a comparar con el objeto `_variant_t`.  
  
 `pSrc`  
 Puntero a **VARIANT** que se va a comparar con el objeto `_variant_t`.  
  
## Valor devuelto  
 Devuelve **true** si la comparación es positiva; **false** si no.  
  
## Comentarios  
 Compara un objeto `_variant_t` con **VARIANT**, para comprobar la igualdad o desigualdad.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)