---
title: isnormal
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 93e3b8912ddf20bf8e190bb42e8413e6d909bbcc
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703470"
---
# <a name="isnormal"></a>isnormal

Determina si un valor de punto flotante es infinito.

## <a name="syntax"></a>Sintaxis

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

**isnormal** devuelve un valor distinto de cero (**true** en código de C++) si el argumento *x* es finito y no subnormal. **isnormal** devuelve 0 (**false** en código de C++) si el argumento es un NAN, infinito o un subnormales.

## <a name="remarks"></a>Comentarios

**isnormal** es una macro, cuando se compila como C y una función de plantilla en línea cuando se compila como C++.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<math.h> o \<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
