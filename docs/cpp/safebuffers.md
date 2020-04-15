---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365581"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft Specific**

Indica al compilador que no inserte comprobaciones de seguridad de saturación del búfer para una función.

## <a name="syntax"></a>Sintaxis

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Observaciones

La opción del compilador **/GS** hace que el compilador pruebe si hay saturaciones de búfer insertando comprobaciones de seguridad en la pila. Los tipos de estructuras de datos que son aptas para las comprobaciones de seguridad se describen en [/GS (Comprobación](../build/reference/gs-buffer-security-check.md)de seguridad de búfer). Para obtener más información acerca de la detección de saturación de búfer, consulte [Características de seguridad en MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Una revisión manual externo o realizado por un experto para revisar el código puede determinar si una función está protegida de la saturación del búfer. En ese caso, puede suprimir las comprobaciones de seguridad de una función aplicando la palabra clave **__declspec(safebuffers)** a la declaración de función.

> [!CAUTION]
> Las comprobaciones de seguridad del búfer proporcionan una protección de seguridad importante y apenas repercuten en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

## <a name="inline-functions"></a>Funciones insertadas

Una *función principal* puede utilizar una palabra clave [de inserción](inline-functions-cpp.md) para insertar una copia de una *función secundaria.* Si la palabra clave **__declspec(safebuffers)** se aplica a una función, se suprime la detección de saturación de búfer para esa función. Sin embargo, la inserción afecta a la palabra clave **__declspec(safebuffers)** de las siguientes maneras.

Supongamos que se especifica la opción del compilador **/GS** para ambas funciones, pero la función principal especifica la palabra clave **__declspec(safebuffers).** Las estructuras de datos en la función secundaria hacen que sea apta para las comprobaciones de seguridad, y la función no suprime dichas comprobaciones. En este caso:

- Especifique la palabra clave [__forceinline](inline-functions-cpp.md) en la función secundaria para forzar al compilador a insertar esa función independientemente de las optimizaciones del compilador.

- Dado que la función secundaria es apta para comprobaciones de seguridad, las comprobaciones de seguridad también se aplican a la función principal aunque especifique la palabra clave **__declspec (safebuffers).**

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo utilizar la palabra clave **__declspec(safebuffers).**

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

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[en línea, \___inline, _forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
