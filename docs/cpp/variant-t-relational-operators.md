---
title: _variant_t (Operadores relacionales)
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
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
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187575"
---
# <a name="_variant_t-relational-operators"></a>_variant_t (Operadores relacionales)

**Específicos de Microsoft**

Compara dos objetos `_variant_t` para ver si son iguales o no.

## <a name="syntax"></a>Sintaxis

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Parámetros

*varSrc*<br/>
`VARIANT` que se va a comparar con el objeto `_variant_t`.

*pSrc*<br/>
Puntero a la `VARIANT` que se va a comparar con el objeto `_variant_t`.

## <a name="return-value"></a>Valor devuelto

Devuelve **true** si la comparación contiene, **false** en caso contrario.

## <a name="remarks"></a>Observaciones

Compara un objeto `_variant_t` con un `VARIANT`, probando la igualdad o la desigualdad.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_variant_t (Clase)](../cpp/variant-t-class.md)
