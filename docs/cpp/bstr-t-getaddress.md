---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181257"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Específicos de Microsoft**

Libera cualquier cadena existente y devuelve la dirección de una cadena recién asignada.

## <a name="syntax"></a>Sintaxis

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Valor devuelto

Puntero a `BSTR` contenido en `_bstr_t`.

## <a name="remarks"></a>Observaciones

**GetAddress** afecta a todos los objetos `_bstr_t` que comparten un `BSTR`. Más de una `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y el **operador =** .

## <a name="example"></a>Ejemplo

Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo de uso de **GetAddress**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
