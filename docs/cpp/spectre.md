---
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 40eee25dec867ae3fce7a6b2d4715f0be81bfe76
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926367"
---
# <a name="spectre"></a>spectre

**Específicos de Microsoft**

Indica al compilador que no inserte instrucciones de barrera de ejecución especulativa de Spectre Variant 1 para una función.

## <a name="syntax"></a>Sintaxis

> **__declspec( spectre(nomitigation) )**

## <a name="remarks"></a>Comentarios

La opción del compilador [/Qspectre](../build/reference/qspectre.md) hace que el compilador Inserte instrucciones de barrera de ejecución especulativa. Se insertan donde el análisis indica que existe una vulnerabilidad de seguridad Spectre Variant 1. Las instrucciones específicas emitidas dependen del procesador. Aunque estas instrucciones deben tener un impacto mínimo en el tamaño o el rendimiento del código, puede haber casos en los que el código no se vea afectado por la vulnerabilidad y requiere un rendimiento máximo.

El análisis experto podría determinar que una función es segura desde un defecto de la comprobación de límites de Spectre Variant 1. En ese caso, puede suprimir la generación de código de mitigación dentro de una función `__declspec(spectre(nomitigation))` aplicando a la declaración de función.

> [!CAUTION]
> Las instrucciones de barrera de ejecución especulativa de **/Qspectre** proporcionan una protección de seguridad importante y tienen un efecto insignificante en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

## <a name="example"></a>Ejemplo

En el siguiente código se muestra cómo usar `__declspec(spectre(nomitigation))`:

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
