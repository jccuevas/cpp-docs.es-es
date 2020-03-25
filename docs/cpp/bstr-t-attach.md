---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 3b52661097ca1feab4c8045be240e4138a0c0f21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190669"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Específicos de Microsoft**

Vincula un contenedor `_bstr_t` a un `BSTR`.

## <a name="syntax"></a>Sintaxis

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parámetros

*s*<br/>
`BSTR` que se va a asociar con, o asignar a, la variable `_bstr_t`.

## <a name="remarks"></a>Observaciones

Si `_bstr_t` se ha asociado previamente a otro `BSTR`, `_bstr_t` limpiará el recurso de `BSTR`, si ninguna otra variable `_bstr_t` está utilizando `BSTR`.

## <a name="example"></a>Ejemplo

Vea [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo de uso de **Attach**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
