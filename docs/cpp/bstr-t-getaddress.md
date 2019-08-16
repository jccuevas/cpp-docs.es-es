---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393901"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Específicos de Microsoft**

Libera cualquier cadena existente y devuelve la dirección de una cadena recién asignada.

## <a name="syntax"></a>Sintaxis

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Valor devuelto

Puntero a `BSTR` contenido en `_bstr_t`.

## <a name="remarks"></a>Comentarios

**GetAddress** afecta a todos los `_bstr_t` objetos que comparten un `BSTR`. Más de un `_bstr_t` puede compartir un `BSTR` mediante el uso del constructor de copias y **operador =**.

## <a name="example"></a>Ejemplo

Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con **GetAddress**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)