---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618054"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR

**Específicos de Microsoft**

Señala al principio del objeto `BSTR` incluido en `_bstr_t`.

## <a name="syntax"></a>Sintaxis

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Valor devuelto

Principio del objeto `BSTR` incluido en `_bstr_t`.

## <a name="remarks"></a>Comentarios

**GetBSTR** afecta a todos los `_bstr_t` objetos que comparten un `BSTR`. Más de un `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y **operador =**.

## <a name="example"></a>Ejemplo

Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con **GetBSTR**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)