---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 473a838a48ed6523ce78d0bc8128dd83636c81d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267388"
---
# <a name="safebuffers"></a>safebuffers

**Específicos de Microsoft**

Indica al compilador que no inserte comprobaciones de seguridad de saturación del búfer para una función.

## <a name="syntax"></a>Sintaxis

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Comentarios

El **/GS** opción del compilador hace que el compilador comprobar las saturaciones de búfer mediante la inserción de comprobaciones de seguridad en la pila. Se describen los tipos de estructuras de datos que son aptos para las comprobaciones de seguridad en [/GS (comprobación de seguridad del búfer)](../build/reference/gs-buffer-security-check.md). Para obtener más información acerca de la detección de saturación del búfer, vea [características de seguridad de MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Una revisión manual externo o realizado por un experto para revisar el código puede determinar si una función está protegida de la saturación del búfer. En ese caso, puede suprimir las comprobaciones de seguridad para una función aplicando el **__declspec (safebuffers)** palabra clave para la declaración de función.

> [!CAUTION]
>  Las comprobaciones de seguridad del búfer proporcionan una protección de seguridad importante y apenas repercuten en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

## <a name="inline-functions"></a>Funciones insertadas

Un *función principal* puede usar un [inserción](inline-functions-cpp.md) palabra clave para insertar una copia de un *función secundaria*. Si el **__declspec (safebuffers)** palabra clave se aplica a una función, detección de saturación del búfer se suprime para esa función. Sin embargo, inlining afecta a la **__declspec (safebuffers)** palabra clave de las maneras siguientes.

Supongamos que el **/GS** se especificó la opción del compilador para ambas funciones, pero la función principal especifica la **__declspec (safebuffers)** palabra clave. Las estructuras de datos en la función secundaria hacen que sea apta para las comprobaciones de seguridad, y la función no suprime dichas comprobaciones. En este caso:

- Especifique el [__forceinline](inline-functions-cpp.md) palabra clave en la función secundaria para forzar el compilador inserte esa función independientemente de las optimizaciones del compilador.

- Dado que la función secundaria es apta para las comprobaciones de seguridad, las comprobaciones de seguridad también se aplican a la función principal, aunque especifique el **__declspec (safebuffers)** palabra clave.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **__declspec (safebuffers)** palabra clave.

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

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)