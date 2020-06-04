---
title: float_control (pragma)
description: Describe el uso y los efectos de la Directiva pragma float_control. La Directiva float_control controla el estado de la semántica precisa de punto flotante y la semántica de excepción en tiempo de ejecución.
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 5f907bfeb3f92f788fe951854ddc32accc83ae03
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166789"
---
# <a name="float_control-pragma"></a>float_control (pragma)

Especifica el comportamiento de punto flotante de una función.

## <a name="syntax"></a>Sintaxis

> **#pragma float_control**\
> **#pragma float_control (preciso,** { **on** | **OFF** } [ **, inserte** ] **)** \
> **#pragma float_control (excepto,** { **on** | **OFF** } [ **, inserte** ] **)** \
> **#pragma float_control (** { **inserte** | **pop** } **)**

## <a name="options"></a>Opciones

**preciso**, **en** | **desactivado**,\ de **extracción**
Especifica si se debe habilitar (**on**) o deshabilitar (**desactivada**) semántica de punto flotante precisa. Para obtener información sobre las diferencias con la opción de compilador **/FP: precise** , vea la sección Comentarios. El token de **extracción** opcional envía la configuración actual de **float_control** en la pila interna del compilador.

**excepto**, **en** | **desactivado**,\ de **extracción**
Especifica si se debe habilitar (**on**) o deshabilitar (**desactivada**) la semántica de excepción de punto flotante. El token de **extracción** opcional envía la configuración actual de **float_control** en la pila interna del compilador.

**salvo** que solo se puede establecer en **on** cuando **precise** también está establecido en **on**.

\ de **extracción**
Envía el valor de **float_control** actual a la pila interna del compilador.

\ **pop**
Quita el valor **float_control** de la parte superior de la pila interna del compilador y lo convierte en el nuevo valor de **float_control** .

## <a name="remarks"></a>Observaciones

La pragma **float_control** no tiene el mismo comportamiento que la opción del compilador [/FP](../build/reference/fp-specify-floating-point-behavior.md) . La pragma **float_control** solamente rige parte del comportamiento de punto flotante. Se debe combinar con las pragmas [fp_contract](../preprocessor/fp-contract.md) y [fenv_access](../preprocessor/fenv-access.md) para volver a crear las opciones del compilador **/FP** . En la tabla siguiente se muestra la configuración de pragma equivalente para cada opción del compilador:

| | float_control (preciso, \*) | float_control (excepto, \*) | fp_contract (\*) | fenv_access (\*) |
|-|-|-|-|-|
| /fp:strict             | en  | en  | apagado | en  |
| /FP: precise            | en  | apagado | en  | apagado |
| /fp:fast               | apagado | apagado | en  | apagado |

En otras palabras, puede que tenga que usar varias directivas pragma en combinación para emular las opciones de línea de comandos **/FP: Fast**, **/FP: precise**y **/FP: STRICT** .

Existen restricciones en cuanto a cómo se pueden usar las pragmas de punto flotante **float_control** y **fenv_access** en combinación:

- Solo se puede usar **float_control** para establecer **excepto** **en on** si se habilita la semántica precisa. La semántica precisa se puede habilitar mediante el **float_control** pragma o mediante las opciones de compilador **/FP: precise** o **/FP: STRICT** .

- No se puede usar **float_control** para desactivar la **precisión** cuando se habilita la semántica de excepción, ya sea mediante una pragma **float_control** o una opción de compilador **/FP: Except** .

- No se puede habilitar **fenv_access** a menos que se habilite la semántica precisa, ya sea mediante una pragma **float_control** o una opción del compilador.

- No puede usar **float_control** para desactivar la **precisión** cuando **fenv_access** está habilitada.

Estas restricciones significan que el orden de algunas pragmas de punto flotante es significativo. Para pasar de un modelo rápido a un modelo estricto mediante pragmas, use el código siguiente:

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

Para pasar de un modelo estricto a un modelo rápido mediante el **float_control** pragma, use el código siguiente:

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

Si no se especifica ninguna opción, **float_control** no tiene ningún efecto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo detectar una excepción de punto flotante de desbordamiento mediante pragma **float_control**.

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>Consulte también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
