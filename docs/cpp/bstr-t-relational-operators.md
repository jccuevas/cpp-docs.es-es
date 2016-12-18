---
title: "_bstr_t (Operadores relacionales) | Microsoft Docs"
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
  - "_bstr_t::operator>"
  - "_bstr_t::operator=="
  - "_bstr_t::operator>="
  - "_bstr_t::operator!="
  - "_bstr_t::operator<"
  - "_bstr_t::operator<="
  - "_bstr_t::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= (operador)"
  - "< (operador), comparar objetos específicos"
  - "<= (operador), con objetos específicos"
  - "== (operador), con objetos específicos de Visual C++"
  - "> (operador), comparar objetos específicos"
  - ">= (operador), comparar objetos específicos"
  - "operador !=, operadores relacionales"
  - "operador <, bstr"
  - "operador <=, bstr"
  - "operador ==, bstr"
  - "operador >, bstr"
  - "operador >=, bstr"
  - "operator!=, operadores relacionales"
  - "operator<, bstr"
  - "operator<=, bstr"
  - "operator==, bstr"
  - "operator>=, bstr"
  - "operadores relacionales, _bstr_t (clase)"
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t (Operadores relacionales)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Compara dos objetos `_bstr_t`.  
  
## Sintaxis  
  
```  
  
      bool operator!( ) const throw( );   
bool operator==(  
   const _bstr_t& str   
) const throw( );  
bool operator!=(  
   const _bstr_t& str   
) const throw( );  
bool operator<(  
   const _bstr_t& str   
) const throw( );  
bool operator>(  
   const _bstr_t& str   
) const throw( );  
bool operator<=(  
   const _bstr_t& str   
) const throw( );  
bool operator>=(  
   const _bstr_t& str   
) const throw( );  
```  
  
## Comentarios  
 Estos operadores comparan dos objetos `_bstr_t` lexicográficamente.  Los operadores devuelven **true** si las comparaciones se sostienen; si no, devuelven **false**.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)