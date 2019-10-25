---
title: asin, asinf, asinl
ms.date: 04/05/2018
api_name:
- asinf
- asinl
- asin
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1e70c9b2187b97d3dea589c1757081da8bf2bd10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943649"
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

La función **Asin** devuelve el arcoseno (la función sinusoidal inversa) de *x* en el intervalo-π/2 a π/2 radianes.

De forma predeterminada, si *x* es menor que-1 o mayor que 1, **Asin** devuelve un valor indefinido.

|Entrada|Excepción SEH|Excepción de Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**INVALID**|**_DOMAIN**|
|± **QNAN**, **IND**|ninguna|**_DOMAIN**|
|&#124;x&#124;>1|**INVALID**|**_DOMAIN**|

## <a name="remarks"></a>Comentarios

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **Asin** con valores **float** y **Long** **Double** . En un programa de C, **Asin** siempre toma y devuelve un **valor Double**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|
|-------------|---------------------|-|
|**asin**, **asinf**, **asinl**|\<math.h>|\<cmath> o \<math.h>|

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
