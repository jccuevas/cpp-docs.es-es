---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749701"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Microsoft Specific**

Vincula un contenedor `_bstr_t` a un `BSTR`.

## <a name="syntax"></a>Sintaxis

```cpp
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

Consulte [_bstr_t::Asignar](../cpp/bstr-t-assign.md) para obtener un ejemplo mediante **Adjuntar**.

**END Microsoft Specific**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)
