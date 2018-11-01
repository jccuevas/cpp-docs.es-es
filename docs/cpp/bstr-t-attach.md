---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604443"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

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

## <a name="remarks"></a>Comentarios

Si `_bstr_t` se ha asociado previamente a otro `BSTR`, `_bstr_t` limpiará el recurso de `BSTR`, si ninguna otra variable `_bstr_t` está utilizando `BSTR`.

## <a name="example"></a>Ejemplo

Consulte [_bstr_t:: Assign](../cpp/bstr-t-assign.md) para obtener un ejemplo con **adjuntar**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_bstr_t (Clase)](../cpp/bstr-t-class.md)