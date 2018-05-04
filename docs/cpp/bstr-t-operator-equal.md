---
title: _bstr_t::operator = | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5537f4ad3abbac9686272e15d06bfa5df0bfca6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
 *S1*  
 Un objeto `_bstr_t` que se va a asignar a un objeto `_bstr_t` existente.  
  
 *S2*  
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