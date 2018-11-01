---
title: asin, asinf, asinl
ms.date: 04/05/2018
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 20a2ffc37ea666207b9558cb5c282c414cfd4838
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476055"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Calcula el arcoseno.

## <a name="syntax"></a>Sintaxis

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor cuyo arcoseno se va a calcular.

## <a name="return-value"></a>Valor devuelto

El **asin** función devuelve el arco seno (la función seno inverso) de *x* en el intervalo de - π/2 a π/2 radianes.

De forma predeterminada, si *x* es menor que -1 o mayor que 1, **asin** devuelve un valor indefinido.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NO VÁLIDO**|**_DOMINIO**|
|+ **QNAN**, **IND**|ninguna|**_DOMINIO**|
|&#124;x&#124;>1|**NO VÁLIDO**|**_DOMINIO**|

## <a name="remarks"></a>Comentarios

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **asin** con **float** y **largo** **doble** valores. En un programa C, **asin** siempre toma y devuelve un **doble**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf**, **asinl**|\<math.h>|\<cmath> o \<math.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, consulte [acos, acosf, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
