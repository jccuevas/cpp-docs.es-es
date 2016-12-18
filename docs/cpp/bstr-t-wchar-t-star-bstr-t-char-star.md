---
title: "_bstr_t::wchar_t*, _bstr_t::char* | Microsoft Docs"
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
  - "_bstr_t::wchar_t*"
  - "_bstr_t::char*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operador char*"
  - "operador wchar_t*"
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::wchar_t*, _bstr_t::char*
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Devuelve los caracteres BSTR como matriz de caracteres estrechos o anchos.  
  
## Sintaxis  
  
```  
  
      operator const wchar_t*( ) const throw( );   
operator wchar_t*( ) const throw( );   
operator const char*( ) const;   
operator char*( ) const;  
```  
  
## Comentarios  
 Estos operadores pueden utilizarse para extraer los datos de caracteres encapsulados por el objeto `BSTR`.  La asignación de un nuevo valor al puntero devuelto no modifica los datos BSTR originales.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)