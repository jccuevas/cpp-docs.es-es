---
title: _bstr_t::operator = | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
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
ms.openlocfilehash: 445c18ece9b998d5cfa75a1c9fe5bde3b60b2e52
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Específicos de Microsoft**  
  
 Asigna un nuevo valor a un objeto `_bstr_t` existente.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *s1*  
 Un objeto `_bstr_t` que se va a asignar a un objeto `_bstr_t` existente.  
  
 *s2*  
 Una cadena multibyte que se va a asignar a un objeto `_bstr_t` existente.  
  
 `s3`  
 Una cadena Unicode que se va a asignar a un objeto `_bstr_t` existente.  
  
 `var`  
 Un objeto `_variant_t` que se va a asignar a un objeto `_bstr_t` existente.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="example"></a>Ejemplo  
 Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo del uso de `operator=`.  
  
## <a name="see-also"></a>Vea también  
 [_bstr_t (Clase)](../cpp/bstr-t-class.md)
