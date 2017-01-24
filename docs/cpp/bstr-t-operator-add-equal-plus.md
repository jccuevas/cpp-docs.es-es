---
title: "_bstr_t::operator +=, + | Microsoft Docs"
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
  - "_bstr_t::operator+"
  - "_bstr_t::operator+="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "+ (operador), _bstr_t (objetos)"
  - "+= (operador), anexar cadenas"
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator +=, +
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Anexa los caracteres al final del objeto `_bstr_t` o concatena dos cadenas.  
  
## Sintaxis  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### Parámetros  
 *s1*  
 Un objeto `_bstr_t`.  
  
 *s2*  
 Cadena multibyte.  
  
 `s3`  
 Cadena Unicode.  
  
## Comentarios  
 Estos operadores realizan la concatenación de cadenas:  
  
-   **operator\+\=\(**  *s1*  **\)** Anexa los caracteres de la `BSTR` encapsulada de *s1* al final del encapsulado de este objeto `BSTR`.  
  
-   **operator\+\(**  *s1*  **\)** Devuelve la nueva `_bstr_t` que se forma al concatenar la `BSTR` de este objeto con la de *s1*.  
  
-   **operator\+\(**  *s2*  **&#124;**  *s1*  **\)** Devuelve una nueva `_bstr_t` que se forma concatenando una cadena multibyte *s2*, convertida a Unicode, con la `BSTR` encapsulada en *s1*.  
  
-   **operator\+\(**  `s3` **,**  *s1*  **\)** Devuelve una nueva `_bstr_t` que se forma concatenando una cadena Unicode `s3` con la `BSTR` encapsulada en *s1*.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)