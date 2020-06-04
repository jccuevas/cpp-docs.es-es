---
title: optimize (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220517"
---
# <a name="optimize-pragma"></a>optimize (Pragma)

Especifica las optimizaciones para cada función.

## <a name="syntax"></a>Sintaxis

> **#pragma optimizar ("** [ *lista de optimizaciones* ] **",** { **on** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

La pragma Optimize debe aparecer fuera de una función. Surte efecto en la primera función definida después de que se vea la Directiva pragma. Los argumentos **on** y **OFF** activan o desactivan las opciones especificadas en la *lista de optimización* .

La *lista de optimización* puede ser cero o más de los parámetros que se muestran en la tabla siguiente.

### <a name="parameters-of-the-optimize-pragma"></a>Parámetros de la directiva pragma optimize

| Parámetros | Tipo de optimización |
|--------------------|--------------------------|
| **g** | Habilitar optimizaciones globales. |
| **s** o **t** | Especificar secuencias cortas o rápidas de código máquina. |
| **y** | Generar punteros de marco en la pila del programa. |

Estos parámetros son las mismas letras que se usan con las opciones del compilador [/o](../build/reference/o-options-optimize-code.md) . Por ejemplo, la directiva pragma siguiente es equivalente a la opción del compilador `/Os`:

```cpp
#pragma optimize( "s", on )
```

El uso de pragma Optimize con la cadena vacía ( **""** ) es una forma especial de la Directiva:

Cuando se usa el parámetro **OFF** , desactiva todas las optimizaciones, **g**, **s**, **t**e y,OFF.

Cuando se usa el parámetro **on** , se restablecen las optimizaciones a las que se especificaron mediante la opción del compilador [/o](../build/reference/o-options-optimize-code.md) .

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
