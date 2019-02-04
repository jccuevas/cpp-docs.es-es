---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
apiname:
- _finite
- _finitef
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: 1be5aa204a7db3054a49c2e05a8fd77b12ae8a3d
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702757"
---
# <a name="isfinite-finite-finitef"></a>isfinite, _finite, _finitef

Determina si un valor de punto flotante es finito.

## <a name="syntax"></a>Sintaxis

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

El `isfinite` macro y `_finite` y `_finitef` funciones devuelven un valor distinto de cero si *x* es cualquier normal o subnormal valor finito. Devuelven 0 si el argumento es infinito o un NaN. La función de plantilla de C++ en línea `isfinite` se comporta del mismo modo, pero devuelve **true** o **false**.

## <a name="remarks"></a>Comentarios

`isfinite` es una macro, cuando se compila como C y una función de plantilla en línea cuando se compila como C++. El `_finite` y `_finitef` funciones son específicas de Microsoft. La función `_finitef` solo está disponible cuando se compila para las plataformas x86, ARM o ARM64.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> o \<math.h>|\<float.h>, \<math.h>, \<cfloat> o \<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> o \<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
