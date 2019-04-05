---
title: strict_gs_check
ms.date: 11/04/2016
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: b62e1be466e65c0de6fb4eaa33ac6e99915529e6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037810"
---
# <a name="strictgscheck"></a>strict_gs_check

Esta directiva pragma proporciona una comprobación de seguridad mejorada.

## <a name="syntax"></a>Sintaxis

```
#pragma strict_gs_check([push,] on )
#pragma strict_gs_check([push,] off )
#pragma strict_gs_check(pop)
```

## <a name="remarks"></a>Comentarios

Indica al compilador que inserte una cookie aleatoria en la pila de la función para ayudar a detectar algunas categorías de saturación del búfer basada en la pila. De forma predeterminada, el `/GS` (Buffer Security Check) la opción del compilador no inserta una cookie para todas las funciones. Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md).

Debe compilar con `/GS` (Buffer Security Check) para habilitar **strict_gs_check**.

Utilice esta directiva pragma en módulos que estén expuestos a datos potencialmente dañinos. Esta directiva pragma es muy agresiva y se aplica a funciones que quizá no necesiten esta defensa, pero está optimizada para minimizar su efecto sobre el rendimiento de la aplicación resultante.

Incluso si usa esta directiva pragma, debe procurar escribir código seguro. Es decir, asegúrese de que el código no tenga ninguna saturación de búfer. **strict_gs_check** puede proteger la aplicación las saturaciones del búfer que permanezcan en el código.

## <a name="example"></a>Ejemplo

En el código siguiente, se produce una saturación del búfer cuando copiamos una matriz en una matriz local. Cuando se compila este código con `/GS`, se inserta ninguna cookie en la pila, porque el tipo de datos de matriz es un puntero. Agregar el **strict_gs_check** pragma fuerza la cookie de pila en la pila de la función.

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

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/GS (Comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md)