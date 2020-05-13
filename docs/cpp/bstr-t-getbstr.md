---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181218"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Específicos de Microsoft**

Señala al principio del objeto `BSTR` incluido en `_bstr_t`.

## <a name="syntax"></a>Sintaxis

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Valor devuelto

Principio del objeto `BSTR` incluido en `_bstr_t`.

## <a name="remarks"></a>Observaciones

**GetBSTR** afecta a todos los objetos `_bstr_t` que comparten un `BSTR`. Más de una `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y el **operador =** .

## <a name="example"></a>Ejemplo

Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo de uso de **GetBSTR**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
