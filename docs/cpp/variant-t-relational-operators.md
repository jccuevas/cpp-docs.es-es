---
title: Operadores relacionales _variant_t | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 663d8e24af8362de8ea809bc37a68c33d3278bc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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