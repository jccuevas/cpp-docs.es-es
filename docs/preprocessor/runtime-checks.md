---
title: runtime_checks (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: a1c8e6cca27e157818e6ec80182f8fefa112daf1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216608"
---
# <a name="runtime_checks-pragma"></a>runtime_checks (Pragma)

Deshabilita o restaura la configuración de [/RTC](../build/reference/rtc-run-time-error-checks.md) .

## <a name="syntax"></a>Sintaxis

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **restore** | **OFF** } **)**

## <a name="remarks"></a>Comentarios

No se puede habilitar una comprobación en tiempo de ejecución que no se haya habilitado con una opción del compilador. Por ejemplo, si no especifica `/RTCs` en la línea de comandos, al `#pragma runtime_checks( "s", restore)` especificar no se habilitará la comprobación del marco de pila.

La Directiva pragma **runtime_checks** debe aparecer fuera de una función y surte efecto en la primera función definida después de que se vea la Directiva pragma. Los argumentos **restore** y **off** activan o desactivan las opciones especificadas en **runtime_checks** .

Los parámetros **runtime_checks** pueden ser varios o ninguno de los mostrados en la tabla siguiente.

### <a name="parameters-of-the-runtime_checks-pragma"></a>Parámetros de la directiva pragma runtime_checks

| Parámetros | Tipo de comprobación en tiempo de ejecución |
|--------------------|-----------------------------|
| **s** | Habilita la comprobación de pila (marco). |
| **c** | Comunica los casos en que se asigna un valor a un tipo de datos más pequeño y se provoca una pérdida de datos. |
| **u** | Informa cuando se usa una variable antes de que se defina. |

Estos parámetros son los mismos que se usan con `/RTC` la opción del compilador. Por ejemplo:

```cpp
#pragma runtime_checks( "sc", restore )
```

El uso de la directiva pragma **runtime_checks** con la cadena vacía ( **""** ) es una forma especial de la directiva:

- Cuando se usa el parámetro **OFF** , desactiva las comprobaciones de errores en tiempo de ejecución enumeradas en la tabla anterior, OFF.

- Cuando se usa el parámetro restore, restablece las comprobaciones de errores en tiempo de ejecución a las que especificó mediante `/RTC` la opción del compilador.

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
