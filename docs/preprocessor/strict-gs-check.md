---
title: strict_gs_check (Pragma)
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 0b66e87f2280c923d05103fccfcbbc8d32daf3fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216583"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check (Pragma)

Esta directiva pragma proporciona una comprobación de seguridad mejorada.

## <a name="syntax"></a>Sintaxis

> **#pragma strict_gs_check (** [ **inserciones,** ] { **on** | **OFF** } **)** \
> **#pragma strict_gs_check (pop)**

## <a name="remarks"></a>Comentarios

Indica al compilador que inserte una cookie aleatoria en la pila de la función para ayudar a detectar algunas categorías de saturación del búfer basada en la pila. De forma predeterminada, `/GS` la opción del compilador (comprobación de seguridad del búfer) no inserta una cookie para todas las funciones. Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md).

Compile mediante para habilitar **strict_gs_check.** `/GS`

Utilice esta directiva pragma en módulos que estén expuestos a datos potencialmente dañinos. **strict_gs_check** es una directiva pragma agresiva y se aplica a funciones que podrían no necesitar esta defensa, pero está optimizada para minimizar su efecto en el rendimiento de la aplicación resultante.

Incluso si usa esta directiva pragma, debe procurar escribir código seguro. Es decir, asegúrese de que el código no tiene saturaciones de búfer. **strict_gs_check** puede proteger la aplicación de saturaciones del búfer que permanecen en el código.

## <a name="example"></a>Ejemplo

En este ejemplo, se produce una saturación del búfer cuando se copia una matriz en una matriz local. Al compilar este código `/GS`con, no se inserta ninguna cookie en la pila, porque el tipo de datos de la matriz es un puntero. Al agregar el pragma **strict_gs_check** se fuerza la cookie de la pila en la pila de funciones.

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md)
