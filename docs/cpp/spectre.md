---
title: Spectre
ms.date: 1/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 2377a3c23be1e27bfe4f2df23eb00823635fa05d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267263"
---
# <a name="spectre"></a>Spectre

**Específicos de Microsoft**

Indica al compilador que no se va a insertar instrucciones de barrera de ejecución especulativa de variante 1 de Spectre para una función.

## <a name="syntax"></a>Sintaxis

> **__declspec( spectre(nomitigation) )**

## <a name="remarks"></a>Comentarios

El [/qspectre](../build/reference/qspectre.md) opción del compilador hace que el compilador inserta instrucciones de barrera de ejecución especulativa donde análisis indica que existe una vulnerabilidad de seguridad de la variante 1 de Spectre. Las instrucciones específicas que se emiten dependen del procesador. Mientras que estas instrucciones deben tener un impacto mínimo en el tamaño del código o de rendimiento, puede haber casos donde el código no se ve afectado por la vulnerabilidad y necesita el máximo rendimiento.

Análisis experto podría determinar que una función está protegida de un defecto de omisión de comprobación de Spectre variante 1 límites. En ese caso, puede suprimir la generación de código de mitigación dentro de una función aplicando `__declspec(spectre(nomitigation))` a la declaración de función.

> [!CAUTION]
> El **/qspectre** instrucciones de barrera de ejecución especulativa proporcionar protección de seguridad importante y tener un efecto insignificante en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

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
