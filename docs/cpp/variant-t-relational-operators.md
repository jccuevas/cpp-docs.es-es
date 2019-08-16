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
ms.openlocfilehash: e0d26247868440f47c73422510ac0e998f8e8dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403300"
---
# <a name="variantt-relational-operators"></a>_variant_t (Operadores relacionales)

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
Un `VARIANT` va a comparar con el `_variant_t` objeto.

*pSrc*<br/>
Puntero a la `VARIANT` va a comparar con el `_variant_t` objeto.

## <a name="return-value"></a>Valor devuelto

Devuelve **true** si mantiene la comparación, **false** si no es así.

## <a name="remarks"></a>Comentarios

Compara un `_variant_t` objeto con un `VARIANT`, comprobar la igualdad o desigualdad.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_variant_t (Clase)](../cpp/variant-t-class.md)