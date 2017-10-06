---
title: _bstr_t::operator +=, + | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0ba8936df56359523a76992866642521f899af69
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Específicos de Microsoft**  
  
 Anexa los caracteres al final del objeto `_bstr_t` o concatena dos cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *s1*  
 Objeto `_bstr_t`.  
  
 *s2*  
 Cadena multibyte.  
  
 `s3`  
 Cadena Unicode.  
  
## <a name="remarks"></a>Comentarios  
 Estos operadores realizan la concatenación de cadenas:  
  
-   **operador += (***s1***)** anexa los caracteres en el objeto encapsulado `BSTR` de *s1* al final de encapsulado esteobjeto`BSTR`.      
  
-   **Operator + (***s1***)** devuelve el nuevo `_bstr_t` que se forma concatenando este objeto `BSTR` con el de *s1*.      
  
-   **Operator + (***s2***&#124;** *s1***)** devuelve un nuevo `_bstr_t` que se forma concatenando una cadena multibyte *s2*, convertido a Unicode, con el `BSTR` encapsulada en *s1*.          
  
-   **Operator + (** `s3` **,***s1***)** devuelve un nuevo `_bstr_t` que se forma concatenando una cadena Unicode `s3` con el `BSTR` encapsulada en *s1*.        
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)
