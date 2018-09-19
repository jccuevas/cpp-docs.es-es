---
title: Operadores relacionales _variant_t | Microsoft Docs
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
ms.openlocfilehash: 95cb1ac663607f26c4f168c2e98910f5b41963c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040175"
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