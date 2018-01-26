---
title: Spectre | Documentos de Microsoft
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs: C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b515d25d4818cf8b6213a37f3fe78df4f3882a69
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="spectre"></a>Spectre

**Específicos de Microsoft**

Indica al compilador que no se inserten instrucciones de barrera de ejecución especulativa Spectre variante 1 para una función.

## <a name="syntax"></a>Sintaxis

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Comentarios

El [/Qspectre](../build/reference/qspectre.md) opción del compilador, el compilador inserta instrucciones de barrera de ejecución especulativa donde análisis indica que existe una vulnerabilidad de seguridad de variante 1 Spectre. Dependen de las instrucciones específicas que se genera en el procesador. Mientras estas instrucciones deben tener un impacto mínimo en el tamaño del código o de rendimiento, puede haber casos en que el código no se ve afectado por la vulnerabilidad y necesita obtener el máximo rendimiento.

El análisis Expert podría determinar si una función está protegida de un defecto de omisión de comprobación de límites de Spectre variante 1. En ese caso, puede suprimir la generación de código de mitigación dentro de una función aplicando `__declspec(spectre(nomitigation))` a la declaración de función.

> [!CAUTION]
> El **/Qspectre** instrucciones de barrera de ejecución especulativa proporcionar protección de seguridad importante y tener un efecto insignificante en el rendimiento. Por tanto, se recomienda que no las suprima, excepto en el caso poco frecuente de que el rendimiento de una función tenga una importancia crítica y se sepa que la función está segura.

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

[__declspec](../cpp/declspec.md)  
[Palabras clave](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
