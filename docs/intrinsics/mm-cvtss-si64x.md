---
title: _mm_cvtss_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: a3b7ece325d975045046e865e6b090f3f6729558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263339"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x

**Específicos de Microsoft**

Genera el x64 extendidos versión de la convertir valor escalar único precisión número de punto flotante a entero de 64 bits (`cvtss2si`) instrucción.

## <a name="syntax"></a>Sintaxis

```
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

#### <a name="parameters"></a>Parámetros

*value*<br/>
[in] Un `__m128` estructura que contiene los valores de punto flotante.

## <a name="return-value"></a>Valor devuelto

Un entero de 64 bits, el resultado de la conversión del primer valor de punto flotante a entero.

## <a name="requirements"></a>Requisitos

|Función intrínseca|Arquitectura|
|---------------|------------------|
|`_mm_cvtss_si64x`|x64|

**Archivo de encabezado** \<intrin.h >

## <a name="remarks"></a>Comentarios

El primer elemento del valor de la estructura se convierte en un entero y devuelve. Los bits de control de redondeo de MXCSR se usan para determinar el comportamiento de redondeo. El valor predeterminado el modo de redondeo es redondear al más cercano, redondear al número par si la parte decimal es 0,5. Dado que el `__m128` estructura representa un registro XMM, esta función intrínseca toma un valor desde el registro XMM y lo escribe en la memoria del sistema.

Esta rutina solo está disponible como función intrínseca.

## <a name="example"></a>Ejemplo

```
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__m128d](../cpp/m128d.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)