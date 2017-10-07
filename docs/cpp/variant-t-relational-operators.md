---
title: Operadores relacionales _variant_t | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d8bcf9550e3e3f8af1836aa3f6e8747089837142
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="variantt-relational-operators"></a>_variant_t (Operadores relacionales)
**Específicos de Microsoft**  
  
 Compara dos objetos `_variant_t` para ver si son iguales o no.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *varSrc*  
 A **VARIANT** va a comparar con la `_variant_t` objeto.  
  
 `pSrc`  
 Puntero a la **VARIANT** va a comparar con la `_variant_t` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la comparación es positiva, **false** si no es así.  
  
## <a name="remarks"></a>Comentarios  
 Compara una `_variant_t` objeto con un **VARIANT**, comprobar la igualdad o desigualdad.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_variant_t (Clase)](../cpp/variant-t-class.md)
