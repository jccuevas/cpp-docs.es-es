---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 705d3eca67f87e505a147af4984496d3af43dd53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178917"
---
# <a name="safebuffers"></a>safebuffers

**Específicos de Microsoft**

Indica al compilador que no inserte comprobaciones de seguridad de saturación del búfer para una función.

## <a name="syntax"></a>Sintaxis

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Observaciones

La opción del compilador **/GS** hace que el compilador Compruebe las saturaciones del búfer mediante la inserción de comprobaciones de seguridad en la pila. Los tipos de estructuras de datos que son válidos para las comprobaciones de seguridad se describen en [/GS (comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md). Para obtener más información sobre la detección de saturación del búfer, vea [características de seguridad en MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Una revisión manual externo o realizado por un experto para revisar el código puede determinar si una función está protegida de la saturación del búfer. En ese caso, puede suprimir las comprobaciones de seguridad de una función aplicando la palabra clave **__declspec (safebuffers)** a la declaración de función.

> [!CAUTION]
>  Las comprobaciones de seguridad del búfer proporcionan una protección de seguridad importante y apenas repercuten en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

## <a name="inline-functions"></a>Funciones insertadas

Una *función principal* puede usar una [palabra clave](inline-functions-cpp.md) de inserción para insertar una copia de una *función secundaria*. Si se aplica la palabra clave **__declspec (safebuffers)** a una función, se suprime la detección de saturación del búfer para esa función. Sin embargo, la inclusión afecta a la palabra clave **__declspec (safebuffers)** de las siguientes maneras.

Supongamos que se especifica la opción del compilador **/GS** para ambas funciones, pero la función principal especifica la palabra clave **__declspec (safebuffers)** . Las estructuras de datos en la función secundaria hacen que sea apta para las comprobaciones de seguridad, y la función no suprime dichas comprobaciones. En este caso:

- Especifique la palabra clave [__forceinline](inline-functions-cpp.md) en la función secundaria para obligar al compilador a alinear esa función independientemente de las optimizaciones del compilador.

- Dado que la función secundaria es válida para las comprobaciones de seguridad, las comprobaciones de seguridad también se aplican a la función principal aunque especifique la palabra clave **__declspec (safebuffers)** .

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar la palabra clave **__declspec (safebuffers)** .

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
